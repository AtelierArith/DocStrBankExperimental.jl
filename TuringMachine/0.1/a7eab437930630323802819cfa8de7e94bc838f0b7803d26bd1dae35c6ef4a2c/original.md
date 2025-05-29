```
load_program(file_name)
```

Takes a text file containing a Turing program. Please see docs for how to write such a program.

Input

  * `file_name`::string : path of text file containing the Turing program to simulate

Output

  * `program`::Dict{Any,Any} with `m` entries: dictionary with keys of [states,read*cells] and values of [next*state,write_cell,movement]
