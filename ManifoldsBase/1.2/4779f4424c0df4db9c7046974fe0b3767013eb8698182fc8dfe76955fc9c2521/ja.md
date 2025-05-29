```
EmbeddedManifold{𝔽, MT <: AbstractManifold, NT <: AbstractManifold} <: AbstractDecoratorManifold{𝔽}
```

`MT`型の[`AbstractManifold`](@ref) `M`を`NT`型の多様体`N`に明示的に埋め込むための型です。デフォルトでは、埋め込まれた多様体は埋め込まれていると設定されていますが、等長埋め込みでも部分多様体でもありません。

!!! note
    多様体`M`を特定の多様体`N`に埋め込む場合、この型は必要ありません。その場合は、単に[`embed!`](@ref)と[`project!`](@ref)を実装すればよいです。等長埋め込みである場合など、埋め込みに関数を渡すこともできます。その際は[`AbstractDecoratorManifold`](@ref)を使用します。2番目の埋め込み（おそらく非デフォルトと見なされる）についてのみ、この型を考慮して、異なる埋め込み`N`に対して異なる埋め込みおよび射影メソッドをディスパッチする必要があります。


# フィールド

  * `manifold` 埋め込まれた多様体である多様体
  * `embedding` 最初の多様体が埋め込まれている2番目の多様体

# コンストラクタ

```
EmbeddedManifold(M, N)
```

[`AbstractManifold`](@ref) `M`を[`AbstractManifold`](@ref) `N`に埋め込む`EmbeddedManifold`を生成します。
