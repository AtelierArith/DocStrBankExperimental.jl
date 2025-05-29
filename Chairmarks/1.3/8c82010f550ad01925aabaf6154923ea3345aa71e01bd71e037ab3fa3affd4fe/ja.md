```
@b [[init] setup] f [teardown] キーワード...
```

`f`をベンチマークし、最速の[`Sample`](@ref)を返します。

完全な結果には[`@be`](@ref)を使用してください。

`@b args...`は`Chairmarks.summarize(@be args...)`と同等です。詳細については[`@be`](@ref)のドキュメントを参照してください。

# 例

```jldoctest; filter = [r"\d\d?\d?\.\d{3} [μmn]?s( \(.*\))?"=>s"RES"], setup=(using Random)
julia> @b rand(10000) # 関数のベンチマーク
5.833 μs (2 allocs: 78.172 KiB)

julia> @b rand hash # ランダムなFloat64をハッシュするのにどれくらい時間がかかるか？
1.757 ns

julia> @b rand(1000) sort issorted(_) || error() # 同時にベンチマークとテスト
11.291 μs (3 allocs: 18.062 KiB)

julia> @b rand(1000) sort! issorted(_) || error() # BAD! これは同じ配列を繰り返しソートします！
1.309 μs (0.08 allocs: 398.769 bytes)

julia> @b rand(1000) sort! issorted(_) || error() evals=1 # setupとteardownの間に関数が1回だけ実行されるようにevals=1を指定
10.041 μs (2 allocs: 10.125 KiB)

julia> @b rand(10) _ sort!∘rand! issorted(_) || error() # または、ベンチマークされた関数にランダム化を含めて、1回だけ割り当てる
120.536 ns

julia> @b (x = 0; for _ in 1:50; x = hash(x); end; x) # パイプラインの任意の位置に任意の式を使用できます。単純な関数だけではありません。
183.871 ns

julia> @b (x = 0; for _ in 1:5e8; x = hash(x); end; x) # これは長時間実行されるので、1回だけ実行されます（ウォームアップなし）
2.447 s (ウォームアップなし)

julia> @b rand(10) hash,objectid # どのハッシュアルゴリズムが速いですか？[この使用法は実験的です]
(17.256 ns, 4.246 ns)
```
