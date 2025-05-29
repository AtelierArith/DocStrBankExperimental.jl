```
@relocate(df, columns, before = nothing, after = nothing)
```

データフレームの列を再配置します。この関数は、指定された列をデータフレーム内の新しい位置に移動することを可能にし、指定されたターゲット列の前または後に移動できます。`columns`、`before`、および`after`の引数はすべて、tidy選択関数を受け入れます。`before`または`after`のいずれか一方のみを指定する必要があります。どちらも指定されていない場合、選択された列はデータフレームの先頭に移動します。

# 引数

  * `df`: データフレーム。
  * `columns`: 移動する列または列の集合。
  * `before`: (オプション) 指定された列が移動する前の列または列の集合。提供されない場合や`nothing`の場合、この引数は無視されます。
  * `after`: (オプション) 指定された列が移動する後の列または列の集合。提供されない場合や`nothing`の場合、この引数は無視されます。

# 例

```jldoctest
julia> df = DataFrame(A = 1:5, B = 6:10, C = ["A", "b", "C", "D", "E"], D = ['A', 'B','A', 'B','C'],
                      E = 1:5, F = ["A", "b", "C", "D", "E"]);

julia> @relocate(df, where(is_string), before = where(is_integer))
5×6 DataFrame
 Row │ C       F       A      B      E      D    
     │ String  String  Int64  Int64  Int64  Char 
─────┼───────────────────────────────────────────
   1 │ A       A           1      6      1  A
   2 │ b       b           2      7      2  B
   3 │ C       C           3      8      3  A
   4 │ D       D           4      9      4  B
   5 │ E       E           5     10      5  C


julia> @relocate(df, B, C, D, after = E)
5×6 DataFrame
 Row │ A      E      B      C       D     F      
     │ Int64  Int64  Int64  String  Char  String 
─────┼───────────────────────────────────────────
   1 │     1      1      6  A       A     A
   2 │     2      2      7  b       B     b
   3 │     3      3      8  C       A     C
   4 │     4      4      9  D       B     D
   5 │     5      5     10  E       C     E

julia> @relocate(df, B, C, D, after = starts_with("E"))
5×6 DataFrame
 Row │ A      E      B      C       D     F      
     │ Int64  Int64  Int64  String  Char  String 
─────┼───────────────────────────────────────────
   1 │     1      1      6  A       A     A
   2 │     2      2      7  b       B     b
   3 │     3      3      8  C       A     C
   4 │     4      4      9  D       B     D
   5 │     5      5     10  E       C     E

julia> @relocate(df, B:C) # 列を前に持ってくる
5×6 DataFrame
 Row │ B      C       A      D     E      F      
     │ Int64  String  Int64  Char  Int64  String 
─────┼───────────────────────────────────────────
   1 │     6  A           1  A         1  A
   2 │     7  b           2  B         2  b
   3 │     8  C           3  A         3  C
   4 │     9  D           4  B         4  D
   5 │    10  E           5  C         5  E
```
