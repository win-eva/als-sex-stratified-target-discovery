# Machine-Learning Prediction of Phenotypic Rescue Targets in ALS
 
Computational pipeline for sex-stratified ALS drug target discovery, combining
AnswerALS RNA-seq differential expression, CLUE L1000 transcriptomic reversal,
ChEMBL target annotation, and a five-model machine learning consensus ranking
(two PU classifiers, three Open Targets regression models).
 
MRes Drug Design, UCL.
 
## Pipeline
 
Notebooks run in order; each one writes files the next one reads.
 
| Notebook | Purpose |
|---|---|
| [`01_data_analysis.ipynb`](scripts/01_data_analysis.ipynb) | Annotates the raw AnswerALS count matrix with gene symbol/biotype, checks donor and sample structure |
| [`02_preprocessing.ipynb`](scripts/02_preprocessing.ipynb) | Collapses to one sample per donor, classifies donor sex from expression, runs PyDESeq2, builds the CLUE query signature |
| [`03_phenotypic_rescue.ipynb`](scripts/03_phenotypic_rescue.ipynb) | Loads CLUE reversal results, ranks compounds, annotates targets via ChEMBL |
| [`04_ml_script.ipynb`](scripts/04_ml_script.ipynb) | Builds the feature matrix, trains the five models, produces the cross-model consensus target list |
 
## Data Availability
 
Raw and processed AnswerALS RNA-seq data are not included in this repository.
Access requires a Data Use Agreement with the AnswerALS consortium. See
https://dataportal.answerals.org.

CLUE's files and outputs require registration. `compoundinfo_beta.txt` is available at [CLUE data dashboard](https://clue.io/releases/data-dashboard).
 
`chembl_n_compounds_cache.csv` and `hpa_ot_cns_cache.csv` are in
`external_annotations/`, included here under their respective attribution licenses.

## Data Sources
 
- AnswerALS ([answerals.org](https://www.answerals.org))
- CLUE / LINCS L1000 ([clue.io](https://clue.io))
- ChEMBL 37 (CC BY-SA 3.0, [ebi.ac.uk/chembl](https://www.ebi.ac.uk/chembl))
- Human Protein Atlas (CC BY 4.0, [proteinatlas.org](https://www.proteinatlas.org))
- Open Targets Platform (CC0 1.0, [targets.opentargets.org](https://targets.opentargets.org))
- STRING (CC BY 4.0, [string-db.org](https://string-db.org))
 
## Environment
 
Notebooks were run in Google Colab. Key dependencies: `pydeseq2`, `scikit-learn`,
`xgboost`, `shap`, `chembl_webresource_client`, `gseapy`. Each notebook installs
its own requirements in its first cell.
