```
array_cache(a::AbstractArray)
```

キャッシュオブジェクトを返し、[`getindex!`](@ref) 関数で使用されます。デフォルトは

```
array_cache(a::T) where T = nothing
```

であり、`uses_hash(T) == Val(false)` となる型 `T` に対して、そして

```
function array_cache(a::T) where T
  hash = Dict{UInt,Any}()
  array_cache(hash,a)
end
```

であり、`uses_hash(T) == Val(true)` となる型 `T` に対して、[`uses_hash`](@ref) 関数を参照してください。後者の場合、型 `T` は次のシグネチャを実装する必要があります。

```
array_cache(hash::Dict,a::AbstractArray)
```

ここで、最初の引数に辞書（すなわち、ハッシュテーブル）を渡します。このハッシュテーブルは、オブジェクト `a` がすでにキャッシュを構築しているかどうかをテストし、次のように再利用するために使用できます。

```
id = objectid(a)
if haskey(hash,id)
  cache = hash[id] # キャッシュを再利用
else
  cache = ... # 必要に応じて新しいキャッシュを構築
  hash[id] = cache # ハッシュテーブルにキャッシュを登録
end
```

このメカニズムは、例えば、複雑な遅延操作ツリーにおける中間結果を再利用するために必要です。マルチスレッド計算では、レースコンディションを避けるために、スレッドごとに異なるハッシュテーブルを使用する必要があります。
