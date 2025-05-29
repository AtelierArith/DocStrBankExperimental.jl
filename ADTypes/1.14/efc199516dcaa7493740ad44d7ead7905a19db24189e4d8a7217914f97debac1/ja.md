```
AutoSparse{D,S,C}
```

スパースヤコビ行列とヘッセ行列を扱うためにADTypes.jlオブジェクトをラップします。

# フィールド

  * `dense_ad::D`: 基本となるADパッケージで、[`AbstractADType`](@ref)をサブタイプ化しています。
  * `sparsity_detector::S`: スパースパターン検出器で、[`AbstractSparsityDetector`](@ref)をサブタイプ化しています。
  * `coloring_algorithm::C`: 彩色アルゴリズムで、[`AbstractColoringAlgorithm`](@ref)をサブタイプ化しています。

# コンストラクタ

```
AutoSparse(
    dense_ad;
    sparsity_detector=ADTypes.NoSparsityDetector(),
    coloring_algorithm=ADTypes.NoColoringAlgorithm()
)
```
