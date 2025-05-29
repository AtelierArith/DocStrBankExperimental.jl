```
fix_unbalanced_name(s::String) => String
```

Recursive function that fixes unbalanced parentheses in a string, and returns balanced string.

# Example:

```
julia> my_s = "DG(18:1(/1(8:1)";  
julia> fix_unbalanced_name(my_s) 
"DG(18:1/18:1)"  
julia> my_s = "DG(18:1/18:1))";
julia> fix_unbalanced_name(my_s) 
"DG(18:1/18:1)" 
julia> my_s = "DG(((((18:1/18:1))";
julia> fix_unbalanced_name(my_s) 
"DG((18:1/18:1))" 
```
