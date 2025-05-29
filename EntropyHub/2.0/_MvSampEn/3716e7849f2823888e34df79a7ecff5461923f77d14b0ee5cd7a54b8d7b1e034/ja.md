```
MSamp, B0, Bt, B1 = MvSampEn(Data)
```

`MSamp`（多変量サンプルエントロピー推定値）と、平均一致遅延ベクトル数（`m`：`B0`；共同合計 `m+1` サブスペース：`Bt`；すべての可能な `m+1` サブスペース：`B1`）を、デフォルトのパラメータを使用して `Data` の M 個の多変量系列から返します：埋め込み次元 = 2*ones(M)、時間遅延 = ones(M)、半径閾値 = 0.2、対数 = 自然、データ正規化 = false

!!! note
    `MSamp` として返されるエントロピー値は、「フル」メソッド [すなわち -log(Bt/B0)] を使用して推定され、これは [1][2] で適用される埋め込み空間のすべての可能な `m+1` 拡張にわたって遅延ベクトルを比較します。従来のサンプルエントロピーの定義とは異なり、この方法は 0 の下限を提供しません!! したがって、確率過程に対しても多変量サンプルエントロピーの負のエントロピー値を得ることが可能です...

    代わりに、個々の `m+1` サブスペース (B1) の一致ベクトルの平均数を使用して、0 の下限を保証する「ナイーブ」メソッドを介して `MSamp` を計算することができます（例：-log(B1(1)/B0））、またはすべての `m+1` サブスペースの平均 [すなわち -log(mean(B1)/B0)]。

    埋め込みプロセスのポイント数を最大化するために、このアルゴリズムは N - max(m * tau) 遅延ベクトルを使用し、***N-max(m) * max(tau)*** は [1][2] で使用されるものではありません。


---

```
MSamp, B0, Bt, B1 = MvSampEn(Data::AbstractArray{T} where T<:Real; m::Union{AbstractArray{T} where T<:Int, Nothing}=nothing, tau::Union{AbstractArray{T} where T<:Int, Nothing}=nothing, r::Real=0.2, Logx::Real=exp(1), Norm::Bool=false)
```

指定されたキーワード引数を使用して、`Data` の M 個の多変量データ系列から推定された多変量サンプルエントロピー推定値 (`MSamp`) を返します：

# 引数：

`Data`  - 多変量データセット、N (>10) 観測（行）と M（列）単変量データ系列の NxM 行列

`m`     - 埋め込み次元、M 個の正の整数のベクトル

`tau`   - 時間遅延、M 個の正の整数のベクトル

`r`     - 半径距離閾値、正のスカラー  

`Logx`  - 対数の底、正のスカラー 

`Norm`  - すべての M 系列を単位分散に正規化するかどうか、ブール値

# 参照： `SampEn`, `XSampEn`, `SampEn2D`, `MSEn`, `MvFuzzEn`, `MvPermEn`

# 参考文献：

```
[1] Ahmed Mosabber Uddin, Danilo P. Mandic
    "Multivariate multiscale entropy: A tool for complexity
    analysis of multichannel data."
    Physical Review E 84.6 (2011): 061918.

[2] Ahmed Mosabber Uddin, Danilo P. Mandic
    "Multivariate multiscale entropy analysis."
    IEEE signal processing letters 19.2 (2011): 91-94.
```
