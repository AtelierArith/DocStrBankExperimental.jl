```
@be [[init] setup] f [teardown] keywords...
```

関数 `f` をベンチマークし、結果を [`Benchmark`](@ref) として返します。

省略形の結果には [`@b`](@ref) を使用します。

# 位置引数パイプライン構文

4つの位置引数はパイプラインを形成し、各引数の戻り値が次の引数に渡されます。したがって、パイプライン内の最初の式は無引数関数でなければなりません。`rand` のようなシンボルを使用すると、それは関数として解釈され、通常通り呼び出されます。他の式を使用すると、それは無引数関数の本体として解釈されます。例えば、`@be rand(10)` の場合、ベンチマークされる関数は `() -> rand(10)` です。

パイプライン内の後の位置は単項関数でなければなりません。最初の関数と同様に、関数または式を提供できます。ただし、ルールは少し異なります。提供する式に `_` が右辺値として含まれている場合（そうでなければエラーになります）、それは単項関数として解釈され、パイプライン内の前の関数の結果でそのような `_` の出現が置き換えられます。例えば、`@be rand(10) sort(_, rev=true)` の場合、セットアップ関数は `() -> rand(10)` で、主関数は `x -> sort(x, rev=true)` です。提供する式に `_` が右辺値として含まれていない場合、それは関数を生成するものと見なされ、パイプライン内の前の関数の結果で呼び出されます。例えば、`@be rand(10) sort!∘shuffle!` の場合、主関数は単に `sort!∘shuffle!` で、前処理は受けません。`@macroexpand` は特定のケースで何が起こっているのかを明らかにするのに役立ちます。

# 位置引数の曖昧さの解消

`setup`、`teardown`、および `init` はオプションであり、その優先順位で解析され、次のような形式が可能です：

```
@be f
@be setup f
@be setup f teardown
@be init setup f teardown
```

アンダースコア `_` を使用して他の引数の組み合わせを提供できます。例えば、`teardown` を提供し、`setup` を提供しない場合は次のようにします。

```
@be _ f teardown
```

# キーワード引数

`name=value` 構文を使用してキーワード引数を提供します。これは通常の関数にキーワード引数を提供する方法に似ています。実行を制御するためのキーワード引数は次のとおりです。

  * `evals::Integer` 各サンプルで実行する関数評価の回数。デフォルトは自動キャリブレーションです。
  * `samples::Integer` 取得するサンプルの最大数。デフォルトは無制限で、`evals` を指定しない限り指定できません。`samples = 0` を指定すると、`@be` はウォームアップサンプルのみを実行し、そのサンプルを返します。
  * `seconds::Real` ベンチマークに費やす最大時間。デフォルトは [`Charimarks.DEFAULTS.seconds`](@ref Chairmarks.DEFAULTS) （デフォルトは `0.1`）ですが、`samples` が指定されている場合は、デフォルトで10倍の長さ（デフォルトで1秒）になります。ユーザーは自分のインタラクティブな使用のために `Charimarks.DEFAULTS.seconds` を変更することができ、そのデフォルト値は将来的に変更される可能性があります。時間制限を無効にするには `Inf` に設定します。コンパイル時間は通常、この制限に対してカウントされません。時間制限を尊重するために合理的な努力がなされますが、`samples` が指定されていない場合は常にわずかに（1%未満）超過し、長時間実行される関数をベンチマークする際には大幅に超過する可能性があります。
  * `gc::Bool` ベンチマーク中にガーベジコレクションを無効にするための実験的オプション。デフォルトは [`Charimarks.DEFAULTS.gc`](@ref Chairmarks.DEFAULTS) で、デフォルトは `true` です。ベンチマーク中にガーベジコレクションを無効にするには `false` に設定します。ガーベジコレクションを無効にすると、ガーベジコレクションを必要とするベンチマーク中にメモリ不足エラーが発生する可能性がありますが、ベンチマークの終了後に生き残るメモリリークは発生しないはずです。このオプションは実験的なものであり、将来的に削除されるか、その意味が変更される可能性があります。このオプションはまた、Julia の内部に依存しているため、将来のバージョンの Julia で壊れる可能性があります。

# 補間

位置引数内で標準の補間構文を使用できます。これにより、補間された値はベンチマークの実行時に一度だけ評価され、その評価の実行時間は報告された結果には含まれません。例えば、

```
x = [1,2,3]
@b length($x)
```

は次のように等価です。

```
@b [1,2,3] _ length _
```

# 評価モデル

高レベルでは、この関数の実装は次のようになります。

```
x = init()
results = []
for sample in 1:samples
    y = setup(x)

    t0 = time()

    z = f(y)
    for _ in 2:evals
        f(y)
    end

    push!(results, time()-t0)

    teardown(z)
end
```

したがって、`init` は一度呼び出され、`setup` と `teardown` はサンプルごとに一度呼び出され、`f` はサンプルごとに `evals` 回呼び出されます。

# 実験的機能

カンマ区切りの関数または式のリストを `@be` に渡すことができ、すべてが同時にベンチマークされ、サンプルが交互に取得され、`Benchmark` のタプルが返されます。

!!! warning
    比較ベンチマークは実験的であり、将来のバージョンで削除または変更される可能性があります。


# 例

```jldoctest; filter = [r"\d\d?\d?\.\d{3} [μmn]?s( \(.*\))?"=>s"RES", r"\d+ (sample|evaluation)s?"=>s"### \1"], setup=(using Random)
julia> @be rand(10000) # 関数をベンチマーク
Benchmark: 267 samples with 2 evaluations
 min    8.500 μs (2 allocs: 78.172 KiB)
 median 10.354 μs (2 allocs: 78.172 KiB)
 mean   159.639 μs (2 allocs: 78.172 KiB, 0.37% gc time)
 max    39.579 ms (2 allocs: 78.172 KiB, 99.93% gc time)

julia> @be rand hash # ランダムな Float64 をハッシュするのにどれくらいの時間がかかるか？
Benchmark: 4967 samples with 10805 evaluations
 min    1.758 ns
 median 1.774 ns
 mean   1.820 ns
 max    5.279 ns

julia> @be rand(1000) sort issorted(_) || error() # 同時にベンチマークとテスト
Benchmark: 2689 samples with 2 evaluations
 min    9.771 μs (3 allocs: 18.062 KiB)
 median 11.562 μs (3 allocs: 18.062 KiB)
 mean   14.933 μs (3 allocs: 18.097 KiB, 0.04% gc time)
 max    4.916 ms (3 allocs: 20.062 KiB, 99.52% gc time)

julia> @be rand(1000) sort! issorted(_) || error() # BAD! 同じ配列を繰り返しソートします！
Benchmark: 2850 samples with 13 evaluations
 min    1.647 μs (0.15 allocs: 797.538 bytes)
 median 1.971 μs (0.15 allocs: 797.538 bytes)
 mean   2.212 μs (0.15 allocs: 800.745 bytes, 0.03% gc time)
 max    262.163 μs (0.15 allocs: 955.077 bytes, 98.95% gc time)

julia> @be rand(1000) sort! issorted(_) || error() evals=1 # setup と teardown の間に関数が一度だけ実行されるように evals=1 を指定
Benchmark: 6015 samples with 1 evaluation
 min    9.666 μs (2 allocs: 10.125 KiB)
 median 10.916 μs (2 allocs: 10.125 KiB)
 mean   12.330 μs (2 allocs: 10.159 KiB, 0.02% gc time)
 max    6.883 ms (2 allocs: 12.125 KiB, 99.56% gc time)

julia> @be rand(10) _ sort!∘rand! issorted(_) || error() # または、ベンチマークされた関数にランダム化を含め、1回だけ割り当てる
Benchmark: 3093 samples with 237 evaluations
 min    121.308 ns
 median 126.055 ns
 mean   128.108 ns
 max    303.447 ns

julia> @be (x = 0; for _ in 1:50; x = hash(x); end; x) # パイプライン内の任意の位置に任意の式を使用できます。単純な関数だけでなく。
Benchmark: 3387 samples with 144 evaluations
 min    183.160 ns
 median 184.611 ns
 mean   188.869 ns
 max    541.667 ns

julia> @be (x = 0; for _ in 1:5e8; x = hash(x); end; x) # これは長時間実行されるため、一度だけ実行されます（ウォームアップなし）
Benchmark: 1 sample with 1 evaluation
        2.488 s (ウォームアップなし)

julia> @be rand(10) hash,objectid # どのハッシュアルゴリズムが速いか？ [この使用法は実験的です]
Benchmark: 14887 samples with 436 evaluations
 min    17.106 ns
 median 18.922 ns
 mean   20.974 ns
 max    234.998 ns
Benchmark: 14887 samples with 436 evaluations
 min    4.110 ns
 median 4.683 ns
 mean   4.979 ns
 max    42.911 ns
```
