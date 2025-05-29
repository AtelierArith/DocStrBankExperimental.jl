get*loco*geno(dfG::DataFrame; chromosome*colname::String = "Chr", idx*start::Int = 5)

Returns a vector of genotype matrices based on the chromosome.

# Arguments

  * `dfG` is a dataframe containing genotype values and genotype info such as the chromosome, loci...
  * `chromosome_colname` column name containing chromosome information
  * `idx_start` indicates the first column index containing the genotype values
