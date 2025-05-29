```
run_packmol()
run_packmol(input_file::String)
```

Runs the packmol executable with the input file `input_file`. This will run the classical `http://m3g.iqm.unicamp.br/packmol` program, which is a pre-compiled binary. The input file is a text file with the same syntax as the packmol input files.

If no input file is provided, a file explorer will be opened to choose the  input file. 

To disable the file explorer, set the environment variable `PACKMOL_GUI="false"`.
