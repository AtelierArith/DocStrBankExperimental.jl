```
@window_frame(sql_query, args...)
```

SQLクエリ内のウィンドウ関数のウィンドウフレームを定義し、現在の行に対して計算に含める行の範囲を指定します。

# 引数

  * `sqlquery::SQLQuery`: ウィンドウフレームが適用されるSQLQueryインスタンス。
  * `args...`: フレームの境界を指定する可変数の引数。これらは次のようになります：

      * `from`: フレームの開始点。正の整数または負の整数、0または空であることができます。空の場合、UNBOUNDEDが使用されます。
      * `to`: フレームの終了点。正の整数または負の整数、0または空であることができます。空の場合、UNBOUNDEDが使用されます。
      * `to`または`from`を指定せずに整数が1つだけ提供された場合、それはデフォルトでfromとなり、toはUNBOUNDEDになります。
      * 引数が与えられない場合、両方ともUNBOUNDEDになります。

# 例

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());


julia> df_mem = dt(db, df, "df_view");

julia> @chain df_mem begin
        @group_by groups
        @window_frame(3)
        @mutate(avg = mean(percent))
        #@show_query
       end;

julia> @chain df_mem begin
        @group_by groups
        @window_frame(-3, 3)
        @mutate(avg = mean(percent))
        #@show_query
       end;

julia> @chain df_mem begin
        @group_by groups
        @window_frame(to = -3)
        @mutate(avg = mean(percent))
        #@show_query
        @collect
       end;

julia> @chain df_mem begin
        @group_by groups
        @window_frame(from = -3)
        @mutate(avg = mean(percent))
        #@show_query
        @collect
       end;
```
