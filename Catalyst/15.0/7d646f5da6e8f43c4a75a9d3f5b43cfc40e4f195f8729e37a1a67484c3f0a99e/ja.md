```
@reaction
```

単一の [`Reaction`](@ref) オブジェクトを生成するためのマクロで、`@reaction_network` マクロと似た構文を使用します（ただし、単一の反応のみを許可します）。構文の詳細な紹介は `@reaction_network` の説明にあります。

`@reaction` マクロは、3つの部分からなる単一の行に続きます：

  * 反応が起こる速度。
  * 反応によって消費される任意の数の基質。
  * 反応によって生成される任意の数の生成物。

出力は反応であり（`Reaction` コンストラクタを使用して作成されたものと同様）、以下のように簡単な結合反応を作成し、変数 rx に格納します：

```julia
rx = @reaction k, X + Y --> XY
```

マクロは自動的に `X`、`Y`、`XY` を種として推測し（これらは反応物として現れます）、`k` をパラメータとして推測します（反応物として現れないため）。

`@reaction` マクロは `Reaction` コンストラクタに対してより簡潔な表記を提供します。すなわち、ここでは両方のアプローチを使用して同じ反応を作成し、それらが同一であることを確認します。

```julia
# `@reaction` マクロを使用して反応を作成します。
rx = @reaction k*v, A + B --> C + D

# `Reaction` コンストラクタを使用して反応を作成します。
t = default_t()
@parameters k v
@species A(t) B(t) C(t) D(t)
rx2 = Reaction(k*v, [A, B], [C, D])

# 2つのアプローチが同一の結果をもたらすことを確認します：
rx1 == rx2
```

すでに宣言された記号変数を `@reaction` に補間することが可能です：

```julia
t = default_t()
@parameters k b
@species A(t)
ex = k*A^2 + t
rx = @reaction b*$ex*$A, $A --> C
```

注意：

  * `@reaction` は双方向型反応（`<-->` を使用）や反応のバンドルをサポートしていません（例：`d, (X,Y) --> 0`）。

  * マクロへのJulia変数の補間は `@reaction_network` マクロと同様に機能します。詳細については [The Reaction DSL](@ref dsl_description) チュートリアルを参照してください。
