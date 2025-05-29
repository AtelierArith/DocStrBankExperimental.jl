```
MaternKernel(; ν::Real=1.5, metric=Euclidean())
```

マテーンカーネルの順序 `ν` に関して `metric`。

# 定義

入力 $x, x'$ と距離 $d(\cdot, \cdot)$ に対して、順序 $\nu > 0$ のマテーンカーネルは次のように定義されます。

$$
k(x,x';\nu) = \frac{2^{1-\nu}}{\Gamma(\nu)}\big(\sqrt{2\nu} d(x, x')\big) K_\nu\big(\sqrt{2\nu} d(x, x')\big),
$$

ここで、$\Gamma$ はガンマ関数であり、$K_{\nu}$ は順序 $\nu$ の第二種の修正ベッセル関数です。デフォルトでは、$d$ はユークリッド距離 $d(x, x') = \|x - x'\|_2$ です。

マテーンカーネルを持つガウス過程は、平均二乗の意味で $\lceil \nu \rceil - 1$ 回微分可能です。

!!! note
    順序 ν に関する微分は現在サポートされていません。


関連情報: [`Matern12Kernel`](@ref), [`Matern32Kernel`](@ref), [`Matern52Kernel`](@ref)
