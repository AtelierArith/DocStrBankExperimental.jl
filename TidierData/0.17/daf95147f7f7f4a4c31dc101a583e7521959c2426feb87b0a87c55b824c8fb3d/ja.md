```
 @rename_with(df, fn, exprs...)
```

選択した列名を関数を使用して変更します

# 引数

  * `df`: DataFrame
  * `fn`: 使用したい関数（例えば、TidierStringsのstr*remove*all）
  * `exprs`: カンマで区切られた1つ以上の引用されていない変数名。変数名はデータ内の位置としても使用でき、`x:y`のように変数の範囲を選択できます。変数名は、先頭が一致するものを選択することもできます。空の場合はすべての列がデフォルトになります。

# 例

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
