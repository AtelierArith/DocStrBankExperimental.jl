```
   @summary(df, cols...)
```

数値列に対して、Q1、Q3、最小値、最大値、平均、中央値、欠損値の数を含むデータフレームを返します。

# 引数

  * 'df': データフレーム
  * `cols`: サマリーを実行する列。この引数はオプションであり、指定しない場合はすべての数値列に対してサマリーが実行されます。

# 例

```jldoctest
julia> df = DataFrame(a = [1, 2, 3, 4, 5],
                      b = [missing, 7, 8, 9, 10],
                      c = [11, missing, 13, 14, missing],
                      d = [16.1, 17.2, 18.3, 19.4, 20.5],
                      e = ["a", "a", "a", "a", "a"]);

julia> @summary(df);

julia> @summary(df, (b:d));

julia> @chain df begin
         @summary(b:d)
       end;
```
