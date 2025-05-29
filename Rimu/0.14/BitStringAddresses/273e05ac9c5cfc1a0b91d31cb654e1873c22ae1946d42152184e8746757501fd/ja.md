```
OccupationNumberFS{M,T} <: SingleComponentFockAddress
```

単一成分ボソンファック状態の占有数を格納するアドレス型で、`M` モードを持ちます。占有数は型 `T <: Unsigned` に収まる必要があります。粒子の数はランタイムデータであり、`num_particles(address)` を使用して取得できます。

# コンストラクタ

  * `OccupationNumberFS(val::Integer...)`: 占有数から構築します。`UInt8` に収まるように 256 未満である必要があります。
  * `OccupationNumberFS{[M,T]}(onr)`: 型 `T` の `M` 個の占有数を持つコレクション `onr` から構築します。指定されていない場合、占有数の型 `T` は引数の型から推測されます。
  * `OccupationNumberFS(fs::BoseFS)`: [`BoseFS`](@ref) から構築します。
  * 短縮マクロ [`@fs_str`](@ref) を使用します。中括弧内に有効ビット数を指定します。以下の例を参照してください。

# 例

```jl_doctest
julia> ofs = OccupationNumberFS(1,2,3)
OccupationNumberFS{3, UInt8}(1, 2, 3)

julia> ofs == fs"|1 2 3⟩{8}"
true

julia> num_particles(ofs)
6
```
