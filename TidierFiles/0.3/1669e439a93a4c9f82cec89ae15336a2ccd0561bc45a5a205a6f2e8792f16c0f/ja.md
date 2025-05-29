```
fwf_empty(filepath::String; num_lines::Int=4, col_names=nothing)
```

固定幅フォーマット（FWF）ファイルを分析して、列の幅を自動的に決定し、列名を提供します。

# 引数

  * `filepath`::String: 分析するFWFファイルへのパス。

num_lines::Int=4: 分析のためにファイルの先頭からサンプリングする行数。デフォルトは4です。

  * `col_names`: オプション; 列名を指定する文字列のベクター。提供されない場合、列名はColumn*1、Column*2などとして生成されます。

# 戻り値

  * 2つの要素を含むタプル:
  * 検出された列幅を表す整数のベクター。
  * 列名を表す文字列のベクター。

# 例

```jldoctest
julia> fwf_data = 
       "John Smith   35    12345  Software Engineer   120,000 \nJane Doe     29     2345  Marketing Manager   95,000  \nAlice Jones  42   123456  CEO                 250,000 \nBob Brown    31    12345  Product Manager     110,000 \nCharlie Day  28      345  Sales Associate     70,000  \nDiane Poe    35    23456  Data Scientist      130,000 \nEve Stone    40   123456  Chief Financial Off 200,000 \nFrank Moore  33     1234  Graphic Designer    80,000  \nGrace Lee    27   123456  Software Developer  115,000 \nHank Zuse    45    12345  System Analyst      120,000 ";

julia> open("fwftest.txt", "w") do file
         write(file, fwf_data)
       end;

julia> path = "fwftest.txt";

julia> fwf_empty(path)
([13, 5, 8, 20, 8], ["Column_1", "Column_2", "Column_3", "Column_4", "Column_5"])

julia> fwf_empty(path, num_lines=4, col_names = ["Name", "Age", "ID", "Position", "Salary"])
([13, 5, 8, 20, 8], ["Name", "Age", "ID", "Position", "Salary"])
```
