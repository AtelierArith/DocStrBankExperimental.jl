正方行列 A の近似部分シュア分解を計算します

```
partial_schur, _ = jdqr(A, pairs = 5)
```

次のキーワード引数を受け付けます：

  * `pairs`: 要求されるシュアベクトルと値の数
  * `subspace_dimensions`: 探索サブスペースのサイズを決定する範囲 `min:max`。すべての外部反復で探索サブスペースは `max` サイズに拡張され、その後 `min` サイズにトリミングされます。探索サブスペースがトリミングされると、最良の近似シュアベクトルが保持されます。大きな探索サブスペースは収束を速めますが、計算コストが高くなります。`min` を `pairs` より少し大きく設定することをお勧めします。
  * `max_iter`: 最大ステップ数。アルゴリズムが `max_iter` ステップを超えると、すべてのシュアベクトルの `pairs` に対して収束していない可能性があります。
  * `target`: どの固有値を見つけるかを決定します。オプション：Near(σ) ここで σ は固有値を見つけたい複素平面の近くの複素数；LargestMagnitude(σ)、SmallestMagnitude(σ)、LargestRealPart(σ)、SmallestRealPart(σ)、LargestImaginaryPart(σ)、SmallestImaginaryPart(σ)、ここで σ は複素数 / 教育的な推測です。
  * `tolerance`: シュアベクトルが収束したと見なされる精度、残差ノルムに基づいています。
  * `solver`: 探索サブスペースの拡張に使用される反復補正方程式ソルバー。
  * `verbosity=0` サイレント、`verbosity==1` 進捗バーを表示、`verbosity==2` より詳細なデバッグ出力を表示。
