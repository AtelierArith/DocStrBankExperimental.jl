```
@byrow
```

DataFramesMeta.jl マクロ内のブロードキャスト操作。

`@byrow` は「本物の」Julia マクロではなく、DataFramesMeta によって作成された無名関数が「行ごとに」適用されるべきであることを示す「フラグ」として機能します。

式が `@byrow` で始まる場合、変換の形 `@byrow :y = f(:x)` または `@orderby`、`@subset`、`@with` の形 `@byrow f(:x)` であれば、DataFramesMeta によって作成された無名関数は `DataFrames.ByRow` 関数ラッパーでラップされ、関数が各行で実行されるようにブロードキャストされます。

### 例

```julia
julia> df = DataFrame(a = [1, 2, 3, 4], b = [5, 6, 7, 8]);

julia> @transform(df, @byrow :c = :a * :b)
4×3 DataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      5      5
   2 │     2      6     12
   3 │     3      7     21
   4 │     4      8     32

julia> @subset(df, @byrow :a == 1 ? true : false)
1×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      5
```

複数の操作を行う際に `@byrow` を何度も書くのを避けるために、操作のブロックの最初に `@byrow` を使用することが許可されています。ブロック内のすべての変換は行ごとに操作されます。

```julia
julia> @subset df @byrow begin
           :a > 1
           :b < 5
       end
1×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     2      4
```

### `@eachrow` との比較

再確認すると、`@eachrow` マクロは大まかに次のように変換します。

```julia
@eachrow df begin
    :a * :b
end
```

を

```julia
begin
    function tempfun(a, b)
        for i in eachindex(a)
            a[i] * b[i]
        end
    end
    tempfun(df.a, df.b)
    df
end
```

関数 `*` は行ごとに適用されます。しかし、これらの操作の結果は、Base Julia の `for` ループのようにどこにも保存されません。むしろ、`@eachrow` と `@eachrow!` はデータフレームを返します。

さて、`@byrow` を考えてみましょう。`@byrow` は次のように変換します。

```julia
@with df @byrow begin
    :a * :b
end
```

を

```julia
tempfun(a, b) = a * b
tempfun.(df.a, df.b)
```

`@eachrow` と対照的に、`@with` と `@byrow` の組み合わせはブロードキャストされた乗算のベクトルを返し、データフレームを返しません。

さらに、`@eachrow!` を使用して適用された変換は入力データフレームを変更します。対照的に、`@byrow` は列を更新しません。

```julia
julia> df = DataFrame(a = [1, 2], b = [3, 4]);

julia> @with df @byrow begin
           :a = 500
       end
2-element Vector{Int64}:
 500
 500

julia> df
2×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      3
   2 │     2      4
```

### `@.` と Base ブロードキャストとの比較

Base Julia はブロードキャストマクロ `@.` を提供しており、多くの場合 `@.` と `@byrow` は同等の結果を与えます。しかし、動作には重要な違いがあります。次のセットアップを考えてみましょう。

```julia
df = DataFrame(a = [1, 2], b = [3, 4])
```

  * 制御フロー。`@byrow` は `if ... else` や `a ? b : c` の形の操作を行ごとに適用することを許可します。これらの式は Base Julia ではブロードキャストできません。`@byrow` はまた、`a && b` や `a || b` の形の式を行ごとに適用することを許可しますが、これは Julia のバージョン 1.7 未満では不可能です。

```
julia> @with df @byrow begin
           if :a == 1
               5
           else
               10
           end
       end
2-element Vector{Int64}:
  5
 10

julia> @with df @. begin
           if :a == 1
               5
           else
               10
           end
       end # エラーになります
```

  * 列でないオブジェクトのブロードキャスト。`@byrow` は入力データフレームの列のみを受け入れる無名関数を構築し、その関数をブロードキャストします。したがって、列でない参照オブジェクトはブロードキャストされません。

```julia
julia> df = DataFrame(a = [1, 2], b = [3, 4]);
julia> @with df @byrow :x + [5, 6]
```

はエラーになります。なぜなら、上記の式の `:x` はスカラー `Int` を参照しており、`1 + [5, 6]` を行うことはできません。

一方で

```julia
@with df @. :x + [5, 6]
```

は成功します。なぜなら、`df.x` は 2 要素のベクトルであり、`[5, 6]` も同様だからです。

`transform` ブロック内の `ByRow` はすべての状況で内部的にブロードキャストを使用しないため、データフレーム内の列がカスタムベクトル型であり、カスタムブロードキャストを実装している場合、このカスタム動作は `@byrow` では呼び出されません。

  * 高価な呼び出しのブロードキャスト。Base Julia では、ブロードキャストは最初に呼び出しを評価し、その結果をブロードキャストします。`@byrow` は無名関数を構築し、その関数をデータフレームの各行に対して評価するため、高価な関数は何度も評価されます。

```julia
julia> function expensive()
           sleep(.5)
           return 1
       end;

julia> @time @with df @byrow :a + expensive();
  1.037073 seconds (51.67 k allocations: 3.035 MiB, 3.19% compilation time)

julia> @time @with df :a .+ expensive();
  0.539900 seconds (110.67 k allocations: 6.525 MiB, 7.05% compilation time)

```

この問題は `@.` マクロを使用する際にも発生しますが、`$` を使うことで簡単に修正できます。`$` は現在、列参照をエスケープするために予約されているため、`@byrow` や DataFramesMeta.jl 全体で現在のところ解決策は存在しません。最良の解決策は単に次のようにすることです。

```
@with df begin
    x = expensive()
    :a + x
end
```
