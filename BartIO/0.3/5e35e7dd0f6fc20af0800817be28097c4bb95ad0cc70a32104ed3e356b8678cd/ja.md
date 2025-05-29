`````
bart = wrapper_bart(pathtobart::String)
Args are concatenated at the end of the command.

### output
- bart : a wrapper to call bart from Julia through the python functions from the bart repository.

TO DO :
- add kwargs support like in the python wrapper https://github.com/mrirecon/bart/pull/295

Example :
````
bart = wrapper_bart(pathtobart)
bart(0,"version")

bart(0,"phantom -h")
bart(1,"phantom -k -x128")
````
`````
