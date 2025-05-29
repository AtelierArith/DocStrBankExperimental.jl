This is the calling function for executing the plug reactor with chemistry input files 

# Method-2

plug(input*file::AbstractString, lib*dir::AbstractString; sens= false, surfchem=false, gaschem=false)

  * input_file: the xml input file plug flow reactor configuration
  * lib_dir: the direcrtory in which the data files are present (mechanism file and therm.dat file).
  * sens: sensitivity calculation
  * surfchem : surface chemistry; false implies no surface chemistry calculation
  * gaschem : gasphase chemistry; false implies no gasphase chemistry calculation
