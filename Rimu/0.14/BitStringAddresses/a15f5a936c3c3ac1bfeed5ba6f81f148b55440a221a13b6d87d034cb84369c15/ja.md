```
BoseFS{N,M,S} <: SingleComponentFockAddress
```

`N` 個のスピンレスボソンが `M` モードに存在するフォック状態を表すアドレス型で、[`BitString`](@ref) または [`SortedParticleList`](@ref) をラップします。どちらをラップするかはアドレスの特性に基づいて自動的に選択されます。

# コンストラクタ

  * `BoseFS{[N,M]}(val::Integer...)`: 占有数から `BoseFS{N,M}` を作成します。モードの数 `M` と粒子の数 `N` が提供されている場合、これは型安定です。そうでない場合、`M` と `N` は引数から推測されます。
  * `BoseFS{[N,M]}(onr)`: 占有数表現から `BoseFS{N,M}` を作成します。[`onr`](@ref) を参照してください。`N` と `M` が提供されている場合、かつ `onr` が静的サイズのコレクション（例えば `Tuple` や `SVector`）である場合、これは効率的です。
  * `BoseFS{[N,M]}([M, ]pairs...)`: モードの数 `M` と `mode => occupation_number` ペアを提供します。`M` が型パラメータとして提供されている場合、最初の引数として提供してはいけません。スパースアドレスを作成するのに便利です。`pairs` は複数の引数またはペアのイテレータであることができます。
  * `BoseFS{N,M,S}(bs::S)`: 安全でないコンストラクタ。`bs` 内の粒子の数が `N` と等しいかどうかはチェックしません。
  * [`@fs_str`](@ref): アドレスは時々コンパクトな形式で印刷されます。この表現はコンストラクタとしても使用できます。以下の最後の例を参照してください。

# 例

```jldoctest
julia> BoseFS{6,5}(0, 1, 2, 3, 0)
BoseFS{6,5}(0, 1, 2, 3, 0)

julia> BoseFS([abs(i - 3) ≤ 1 ? i - 1 : 0 for i in 1:5])
BoseFS{6,5}(0, 1, 2, 3, 0)

julia> BoseFS(5, 2 => 1, 3 => 2, 4 => 3)
BoseFS{6,5}(0, 1, 2, 3, 0)

julia> BoseFS{6,5}(i => i - 1 for i in 2:4)
BoseFS{6,5}(0, 1, 2, 3, 0)

julia> fs"|0 1 2 3 0⟩"
BoseFS{6,5}(0, 1, 2, 3, 0)

julia> fs"|b 5: 2 3 3 4 4 4⟩"
BoseFS{6,5}(0, 1, 2, 3, 0)
```

他にも: [`SingleComponentFockAddress`](@ref), [`OccupationNumberFS`](@ref), [`FermiFS`](@ref), [`CompositeFS`](@ref), [`FermiFS2C`](@ref).
