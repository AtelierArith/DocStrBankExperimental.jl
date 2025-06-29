```
  SeisPatchProcess(in,out;<keyword arguments>)
```

Read data from disk, split into multidimensional overlapping patches, apply processes, merge patches with tapers, and write to disk.

Processing of patches can be done in parallel by running the code using (for example): julia -p 2 script_name.jl

Important Notice: You must make declare global variables f and f*param on every processor. You can do this in your main function by typing (for example): @everywhere global f*param = ["style"=>"mxmyhxhy", "Niter"=> 100, "alpha"=>1,"fmax"=>80] @everywhere global f = [SeisPOCS]

f is an array of functions that have the following syntax: d2, h2 = f(d1,h1,f_param), where param is a dictionary (Dict) of parameters for the function.

note that param should contain parameters for the patching and unpatching operations.

to execute the code type:  julia -p 4 my_code.jl where 4 can be replaced     with the number of processors you wish to use. *Credits: A. Stanton*
