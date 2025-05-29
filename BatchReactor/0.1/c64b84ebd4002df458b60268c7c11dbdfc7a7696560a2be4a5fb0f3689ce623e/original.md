This is the calling function for executing the batch reactor with chemistry input files 

# Usage

batch*reactor(input*file::AbstractString, lib_dir::AbstractString; sens= false, surfchem=false, gaschem=false)

  * input_file: the xml input file for batch reactor
  * lib_dir: the direcrtory in which the data files are present. It must be the relative path
  * sens : Boolean to be set as true when used along with the sensitivity code
  * surfchem : Boolean to specify the calculation of surface reaction rates
  * gaschem : Boolean to specify the calculation of gasphase reaction rates
