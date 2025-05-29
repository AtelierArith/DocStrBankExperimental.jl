```
@tally(df, [wt], [sort])
```

1つ以上の変数のユニークな値を集計し、オプションの重み付けを行います。

`@tally()`は、すでにグループ化が行われていることを前提とした`@count()`のための低レベルのヘルパーマクロです。`@chain @tally()`は、概ね`@chain df @summarize(n = n())`と同等です。重み付けされたカウントを行うには`wt`を指定し、要約を`n = n()`から`n = sum(wt)`に切り替えます。

# 引数

  * `df`: DataFrameまたはGroupedDataFrame。
  * `wt`: オプションのパラメータ。行をカウントするのではなく、提供された`wt`変数の合計を計算するために使用されます。
  * `sort`: デフォルトは`false`です。結果を`n`の高い順から低い順にソートするかどうか。

# 例

```jldoctest
julia> df = DataFrame(a = vcat(repeat(["a"], inner = 3),
                           repeat(["b"], inner = 3),
                           repeat(["c"], inner = 1),
                           missing),
                      b = 1:8)
8×2 DataFrame
 Row │ a        b     
     │ String?  Int64 
─────┼────────────────
   1 │ a            1
   2 │ a            2
   3 │ a            3
   4 │ b            4
   5 │ b            5
   6 │ b            6
   7 │ c            7
   8 │ missing      8

julia> @chain df @tally()
1×1 DataFrame
 Row │ n     
     │ Int64 
─────┼───────
   1 │     8

julia> @chain df begin
         @group_by(a)
         @tally()
       end
4×2 DataFrame
 Row │ a        n     
     │ String?  Int64 
─────┼────────────────
   1 │ a            3
   2 │ b            3
   3 │ c            1
   4 │ missing      1

julia> @chain df begin
         @group_by(a)
         @tally(wt = b)
       end
4×2 DataFrame
 Row │ a        n     
     │ String?  Int64 
─────┼────────────────
   1 │ a            6
   2 │ b           15
   3 │ c            7
   4 │ missing      8

julia> @chain df begin
         @group_by(a)
         @tally(wt = b, sort = true)
       end
4×2 DataFrame
 Row │ a        n     
     │ String?  Int64 
─────┼────────────────
   1 │ b           15
   2 │ missing      8
   3 │ c            7
   4 │ a            6       
```
