```
SequentialEx(; simd)
```

シーケンシャルフォールドエグゼキュータ。Folds.jlやFLoops.jlなどのパッケージのAPIに渡して、アルゴリズムをシーケンシャルに実行できます。

参照: [`foldxl`](@ref), [`ThreadedEx`](@ref) および [`DistributedEx`](@ref)。

# キーワード引数

  * `simd`: `true`または`:ivdep`の場合、`Base.@simd`を使用してSIMDを有効にします。`:ivdep`の場合、`@simd ivdep for ... end`バリアントを使用します。このオプションを使用するのが適切な場合については、`Base.@simd`のJuliaマニュアルを参照してください。たとえば、`simd = :ivdep`は、[`Scan`](@ref)のような状態を持つトランスデューサーと一緒に使用してはいけません。`false`（デフォルト）の場合、`Base.@simd`は使用されません。

# 例

```jldoctest
julia> using Folds

julia> Folds.sum(1:3, SequentialEx())
6
```
