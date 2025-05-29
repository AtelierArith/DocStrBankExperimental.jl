```
fix_unbalanced_name(s::String) => String
```

文字列内の不均衡な括弧を修正し、均衡の取れた文字列を返す再帰関数です。

# 例:

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
