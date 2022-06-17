# IRT_Rapture
Pipeline for analysis of IRT Rapture data

1 - Global Ancestry Inference with Confidence Intervals (GetGlobals.sh)
Command: GetGlobals.sh infile.vcf
Output 1: Ancestry estimates and confidence intervals for all individuals
Output 2: An updated set of allele frequency estimates and reference sample sizes (for future runs)

2 - Split or Combine Sampling Reaches (SplitReaches.sh)
Command: SplitCombineReaches.sh infile.vcf popmap.txt
Output 1: An updated popmap file with a new column called "Revised"
Output 2: A log file indicating the p-values from all exact tests for differences in allele frequencies between reaches.

3 - Find problematic samples (FindProblems.sh
Command: FindProblems.sh infile.vcf infile.globalAnc popmap.txt
Output 1: Appends a column called "CrossContam" to the global ancestry output and popmap

4 - Local ancestry inference with Gnomix (GetLAI.sh)
Command: GetLAI.sh infile.vcf 
Output: Lots of stuff

5 - Create ancestry masked VCFs for Ancestry-Specific diversity measures, assignment tests and PCA
Command: MaskVCF.sh ./LAI_OUT_Directory infile.vcf
Output: Four VCF files, 1 for each species

6 - Do ancestry specific PCA
Command: AS-PCA.sh AS-infile.vcf
Output: Eigenvectors from an ancestry specific PCA

7 - Ancestry Specific discriminant analysis of principal components
Command: AS-DAPC.sh eigenvectors.txt reporting_groups unknowns
Output: Assigns ancestry from species X to reporting groups 

8 - Ancestry specific diversity (AS-Diversity.sh)
Command: AS-Diversity.sh AS-infile.vcf
Output: #PM sites, ancestry specific allele frequencies

