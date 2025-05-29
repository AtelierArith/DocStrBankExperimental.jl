This is the calling function for executing the plug reactor with userdefined rate calculation

# Method-1

plug(input*file::AbstractString, lib*dir::AbstractString; sens= false, surfchem=false, gaschem=false)

  * input_file: the xml input file for batch reactor
  * lib_dir: the direcrtory in which the data files are present. It must be the relative path
  * user_defined: A function which calculates the species source terms, to be supplied by the user
