```
@combination SomeMeasure() = multimeasure(f)
@combination SomeMeasure() = multimeasure(f, mode=...)
```

スカラー関数 `(ŷ, y) -> f(ŷ, y)` から複数の測定コンストラクタを生成するための高度なツールです。パラメータ化された関数のバリエーションについては、以下の「拡張」を参照してください。

`f(yhat, y)` がスカラー引数を持つ通常の関数であると仮定すると、上記の呼び出しは、`@combination` が存在しないかのようにほぼ同様に機能しますが、以下の違いと追加のアクションがあります。

*1.* 新しい具体的な測定タイプ `SomeMeasureOnScalars` が追加されます: `sm = SomeMeasureOnScalars()` の場合、`sm(yhat, y) = f(yhat, y)` となります。

*2.* 特に、次のようになります。

```
SomeMeasure() = multimeasure(
    supports_missings_measure(sm),
    mode=mode,
) |> robust_measure |> fussy_measure
```

これにより、`missing` スカラー要素がサポートされ、関連する引数チェックが行われ、重み引数は `nothing` であることができます。

*3.* 追加のマルチターゲットコンストラクタが定義されます:

```
MultitargetSomeMeasure(; atomic_weights=nothing) = multimeasure(
    multimeasure(supports_missings_measure(sm), mode=mode),
    atomic_weights=atomic_weights,
    transform=vec∘collect,
) |> robust_measure |> fussy_measure
```

この測定は、`missing` スカラー要素と `nothing` 重みのサポートが類似しており、引数チェックを行います。特定の種類のテーブルを消費することができます。

*4.* 両方の種類の測定を表示するための表示メソッドがより親しみやすくなります; [`@fix_show`](@ref) を参照してください。

構造上、`measure = SomeMeasure()` であるのは、`measure isa W{<:W<:W{<:W{<:SomeMeasureOnScalars}}}` の場合に限り、`W = StatisticalMeasuresBase.Wrapper` であり、`measure = MultitargetSomeMeasure(; atomic_weights=wts)` であるのは、`measure isa W{<:W{<:W{<:W{<:W{<:SomeMeasureOnScalars}}}}}` の場合に限ります。

# 拡張

提供された式に単一のパラメータを追加でき、これは `f` の第3引数に対応します。特性も宣言でき、これらは `SomeMeasure` に適用され、適切に `MultitargetSomeMeasure` に持ち上げられ、`SomeScalarMeasure` に落とされます。

拡張された構文の例:

```
f(yhat, y, tol) = abs(yhat - y)/max(abs(y), tol)
@combination(
    ProportionalAbsoluteDifference(; tol=eps()) = multimeasure(f),
    observation_scitype = Continuous,     # Union{Missing,Continuous} になります
    orientation=Loss(),
)
```

さらなる説明については、ドキュメントのチュートリアルを参照してください。

!!! note
    このマクロは実験的であり、その動作はパッチおよびマイナーリリースで変更される可能性があります。

