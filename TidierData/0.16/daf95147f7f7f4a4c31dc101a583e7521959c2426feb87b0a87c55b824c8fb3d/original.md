```
 @rename_with(df, fn, exprs...)
```

Renames the chosen column names using a function

# Arguments

  * `df`: a DataFrame
  * `fn`: desired function to (such as str*remove*all from TidierStrings)
  * `exprs`: One or more unquoted variable names separated by commas. Variable names

can also be used as their positions in the data, like `x:y`, to select  a range of variables. Variables names can also be chosen with starts with. Defaults to all columns if empty.

# Examples

```jldoctest
julia> function str_remove_all(column, pattern::String)
         if ismissing(column)
             return column
         end
         patterns = split(pattern, '|')
         for p in patterns
             column = replace(column, strip(p) => "")
         end
         return column
       end;

julia> df = DataFrame(
              term_a = ["apple", "banana", "cherry"],
              document_a = ["doc_1", "doc2", "doc3"],
              _n_ = [1, 2, 3]
            ); 

julia> @rename_with(df, str -> str_remove_all(str, "_a"), !term_a)
3×3 DataFrame
 Row │ term_a  document  _n_   
     │ String  String    Int64 
─────┼─────────────────────────
   1 │ apple   doc_1         1
   2 │ banana  doc2          2
   3 │ cherry  doc3          3
```
