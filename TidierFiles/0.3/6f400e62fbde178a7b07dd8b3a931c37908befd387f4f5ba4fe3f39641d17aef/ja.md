```
read_fwf(filepath::String; num_lines::Int=4, col_names=nothing)
```

固定幅フォーマット（FWF）ファイルをDataFrameに読み込みます。

# 引数

  * `filepath`::String: 読み込むFWFファイルのパス。
  * `widths_colnames`::Tuple{Vector{Int}, Union{Nothing, Vector{String}}}: 2つの要素を含むタプル：       - 各フィールドの幅を指定する整数のベクター。       - オプションで、列名を指定する文字列のベクター。何も指定しない場合、列名はColumn*1、Column*2などとして生成されます。
  * `skip_to`=0: データを読み込む前にスキップするファイルの先頭の行数。
  * `n_max`=nothing: ファイルから読み込む最大行数。何も指定しない場合、すべての行を読み込みます。

# 例

```jldoctest
julia> fwf_data = 
       "John Smith   35    12345  Software Engineer   120,000 \nJane Doe     29     2345  Marketing Manager   95,000  \nAlice Jones  42   123456  CEO                 250,000 \nBob Brown    31    12345  Product Manager     110,000 \nCharlie Day  28      345  Sales Associate     70,000  \nDiane Poe    35    23456  Data Scientist      130,000 \nEve Stone    40   123456  Chief Financial Off 200,000 \nFrank Moore  33     1234  Graphic Designer    80,000  \nGrace Lee    27   123456  Software Developer  115,000 \nHank Zuse    45    12345  System Analyst      120,000 ";

julia> open("fwftest.txt", "w") do file
         write(file, fwf_data)
       end;

julia> path = "fwftest.txt";

julia> read_fwf(path, fwf_empty(path, num_lines=4, col_names = ["Name", "Age", "ID", "Position", "Salary"]), skip_to=3, n_max=3)
3×5 DataFrame
 Row │ Name         Age     ID      Position         Salary  
     │ String       String  String  String           String  
─────┼───────────────────────────────────────────────────────
   1 │ Bob Brown    31      12345   Product Manager  110,000
   2 │ Charlie Day  28      345     Sales Associate  70,000
   3 │ Diane Poe    35      23456   Data Scientist   130,000
```
