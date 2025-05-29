get*loco*geno*info(dfG::DataFrame; chromosome*colname::String = "Chr", idx_info = collect(1:4))

Returns a vector of genotype information dataframes based on the chromosome.

# Arguments

  * `dfG` is a dataframe containing genotype values and genotype info such as the chromosome, loci...
  * `chromosome_colname` column name containing chromosome information
  * `idx_info` indicates columns containing genotype information (e.g., Locus, Mb...)
