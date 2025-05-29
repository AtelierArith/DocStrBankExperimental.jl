# CompositionsBase.jl: `∘`、`⨟`、`compose`、および `opcompose` をエクスポート

## API

```
f ∘ g
g ⨟ f
compose(f, g)
opcompose(g, f)
```

モルフィズムの合成。 `∘` は `Base` で定義された演算子です。 CompositionsBase.jl は逆合成演算子 `⨟` を次のように定義します。

```
⨟(fs...) = ∘(reverse(fs)...)
```

また、ASCII エイリアス `compose` と `opcompose` も定義されています。

`⨟`、`compose`、および `opcompose` はすべて `∘` に基づいて定義されているため、単一引数の呼び出しは恒等関数です。

### 例

```jldoctest README
julia> using CompositionsBase

julia> tuple ∘ inv === compose(tuple, inv) === inv ⨟ tuple === opcompose(inv, tuple)
true

julia> ∘(tuple) === compose(tuple) === ⨟(tuple) === opcompose(tuple) === tuple
true
```
