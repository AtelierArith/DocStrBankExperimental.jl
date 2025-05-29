```
FermiFS{N,M,S} <: SingleComponentFockAddress
```

アドレス型は、`M` モードの同じスピンの `N` フェルミオンのフォック状態を [`BitString`](@ref) または [`SortedParticleList`](@ref) でラップして表現します。どちらをラップするかはアドレスの特性に基づいて自動的に選択されます。

# コンストラクタ

  * `FermiFS{[N,M]}(val::Integer...)`: 占有数から `FermiFS{N,M}` を作成します。モードの数 `M` と粒子の数 `N` が提供されている場合、これは型安定です。そうでない場合、`M` と `N` は引数から推測されます。
  * `FermiFS{[N,M]}(onr)`: 占有数表現から `FermiFS{N,M}` を作成します。[`onr`](@ref) を参照してください。`N` と `M` が提供されている場合、かつ `onr` が静的サイズのコレクション（例えば `Tuple{M}` や `SVector{M}`）である場合、これは効率的です。
  * `FermiFS{[N,M]}([M, ]pairs...)`: モードの数 `M` と `mode => 1` の形式のペアを提供します。`M` が型パラメータとして提供されている場合、最初の引数として提供してはいけません。スパースアドレスを作成するのに便利です。`pairs` は複数の引数またはペアのイテレータであることができます。
  * `FermiFS{N,M,S}(bs::S)`: 安全でないコンストラクタ。`bs` 内の粒子の数が `N` と等しいか、各モードに1つの粒子しか含まれていないかをチェックしません。
  * [`@fs_str`](@ref): アドレスは時々コンパクトな方法で印刷されます。この表現はコンストラクタとしても使用できます。以下の最後の例を参照してください。

# 例

```jldoctest
julia> FermiFS{3,5}(0, 1, 1, 1, 0)
FermiFS{3,5}(0, 1, 1, 1, 0)

julia> FermiFS([abs(i - 3) ≤ 1 for i in 1:5])
FermiFS{3,5}(0, 1, 1, 1, 0)

julia> FermiFS(5, 2 => 1, 3 => 1, 4 => 1)
FermiFS{3,5}(0, 1, 1, 1, 0)

julia> FermiFS{3,5}(i => 1 for i in 2:4)
FermiFS{3,5}(0, 1, 1, 1, 0)

julia> fs"|⋅↑↑↑⋅⟩"
FermiFS{3,5}(0, 1, 1, 1, 0)

julia> fs"|f 5: 2 3 4⟩"
FermiFS{3,5}(0, 1, 1, 1, 0)
```

参照: [`SingleComponentFockAddress`](@ref), [`BoseFS`](@ref), [`CompositeFS`](@ref), [`FermiFS2C`](@ref), [`BitString`](@ref), [`OccupationNumberFS`](@ref).
