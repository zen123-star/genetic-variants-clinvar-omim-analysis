# genetic-variants-clinvar-omim-analysis

> This repository is part of the coursework for **BI-436 Special Topics in Bioinformatics**.

Pathogenicity analysis of 6 genetic and rare disease variants using ClinVar, OMIM, UCSC Genome Browser, ACMG/AMP guidelines, and SnpEff annotation.

---

## Diseases & Variants

| Disease | Gene | Category | ClinVar Classification |
|---|---|---|---|
| Cystic Fibrosis | CFTR | Genetic | Pathogenic |
| Marfan Syndrome | FBN1 | Genetic | Pathogenic |
| Hemophilia A | F8 | Genetic | Pathogenic |
| Tay-Sachs Disease | HEXA | Rare | Pathogenic/Likely Pathogenic |
| Amyotrophic Lateral Sclerosis | SOD1 | Rare | Likely Benign |
| Ellis-van Creveld Syndrome | EVC, EVC2 | Rare | Benign/Likely Benign |

---

## Repository Structure
```
├── genetic_variants.xlsx
├── variants_annotated.vcf
├── snpeff_summary.html
└── README.md
```

---

## ClinVar: Variant Selection

One pathogenic variant was selected per disease from ClinVar (GRCh38). Each variant was chosen based on clinical significance, review status, and relevance to the condition.

| Disease | Variant | Gene | Type |
|---|---|---|---|
| Cystic Fibrosis | NM_000492.4(CFTR):c.-9_14del (p.Met1fs) | CFTR | Deletion |
| Marfan Syndrome | NM_000138.5(FBN1):c.8554_8561delinsTATCAC (p.Asp2852fs) | FBN1 | Deletion |
| Hemophilia A | NM_000132.4(F8):c.2113+461_2113+473del | F8 | Deletion |
| Tay-Sachs Disease | NM_000520.6(HEXA):c.1549dup (p.Leu517fs) | HEXA | Duplication |
| ALS | NC_000021.9:g.31659614G>C | SOD1 | SNV |
| Ellis-van Creveld | NM_147127.5(EVC2):c.122C>A (p.Pro41His) | EVC2 | SNV |

<img width="1892" height="752" alt="image" src="https://github.com/user-attachments/assets/f92bf3bd-aa8f-4e01-9d8e-59aae05e4e1a" />


---

## OMIM: Phenotype Descriptions

Each gene was looked up in OMIM to document gene-phenotype relationships and inheritance patterns.

| Disease | Gene | Inheritance | Key Phenotype |
|---|---|---|---|
| Cystic Fibrosis | CFTR | Autosomal Recessive | Chronic lung infections, pancreatic insufficiency, meconium ileus |
| Marfan Syndrome | FBN1 | Autosomal Dominant | Tall stature, aortic dilation, lens dislocation |
| Hemophilia A | F8 | X-linked Recessive | Prolonged bleeding, hemarthroses, Factor VIII deficiency |
| Tay-Sachs Disease | HEXA | Autosomal Recessive | Progressive neurodegeneration, cherry-red spot, fatal by age 5 |
| ALS | SOD1 | Autosomal Dominant | Progressive motor neuron loss, muscle weakness, paralysis |
| Ellis-van Creveld | EVC, EVC2 | Autosomal Recessive | Short-limb dwarfism, polydactyly, congenital heart defects |



---

## UCSC Genome Browser: AlphaMissense & REVEL

Each variant was located in UCSC Genome Browser (hg38) with AlphaMissense and REVEL tracks set to full.

| Disease | Position | AlphaMissense | REVEL |
|---|---|---|---|
| Cystic Fibrosis | chr7:117,480,082 | No score — frameshift deletion | No score — frameshift deletion |
| Marfan Syndrome | chr15:48,411,041 | High (red) | High (red) |
| Hemophilia A | chrX:154,947,698 | High (red) | High (red) |
| Tay-Sachs Disease | chr15:72,344,107 | High (red) | High (red) |
| ALS | chr21:31,659,614 | No score — intergenic region | No score — intergenic region |
| Ellis-van Creveld | chr4:5,708,392 | Low (light blue) | Low |

AlphaMissense and REVEL only score missense/SNV variants — frameshift and intergenic variants show no score by design.



---

## ACMG/AMP Classification & VCF Annotation

Each variant was classified using ACMG/AMP guidelines and compiled into a VCF file, then annotated using SnpEff.

| Disease | ACMG Criteria | Classification |
|---|---|---|
| Cystic Fibrosis | PVS1, PM2, PP3 | Pathogenic |
| Marfan Syndrome | PVS1, PM2, PP1 | Pathogenic |
| Hemophilia A | PVS1, PM2 | Pathogenic |
| Tay-Sachs Disease | PVS1, PM2, PP3 | Pathogenic |
| ALS | BP4 | Likely Benign |
| Ellis-van Creveld | BP1, BP4 | Benign/Likely Benign |

**SnpEff annotation command:**
```bash
java -jar snpEff.jar download GRCh38.mane.1.0.ensembl
java -jar snpEff.jar GRCh38.mane.1.0.ensembl variants_annotated.vcf > annotated_output.vcf
```

Open `snpeff_summary.html` in any browser to view the full annotation report.


---

## Tools Used

| Tool | Purpose |
|---|---|
| ClinVar | Variant selection and clinical significance |
| OMIM | Gene-phenotype relationships |
| UCSC Genome Browser | AlphaMissense & REVEL pathogenicity scores |
| ACMG/AMP Guidelines | Variant classification |
| SnpEff | VCF functional annotation |
