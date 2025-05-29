```
psnr_equality(threshold=25) -> f
```

ピーク信号対雑音比（PSNR）に基づく等価比較関数を生成します。

返される関数 `f` は、2つの画像 `reference` と `actual` を入力として受け取ります； `f(reference, actual) == true` であれば `psnr(reference, actual) >= threshold` です。

この関数は画像比較に役立ちます；PSNRが高いほど画像の類似性が高くなります。したがって、等価テストの基準を緩和したい場合は、**小さい** 閾値を使用できます。例えば、

```julia
@test_reference "references/camera.png" testimage("cameraman") by=psnr_equality(20)
```
