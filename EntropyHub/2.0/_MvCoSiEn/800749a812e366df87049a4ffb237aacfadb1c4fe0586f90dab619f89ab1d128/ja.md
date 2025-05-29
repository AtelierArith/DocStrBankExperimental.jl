```
MCoSi, Bm = MvCoSiEn(Data)
```

多変量コサイン類似度エントロピー推定値（`MCoSi`）と、デフォルトのパラメータを使用して`Data`内のM個の多変量シーケンスに対して推定された対応する全体確率（`Bm`）を返します：埋め込み次元 = 2*ones(M)、時間遅延 = ones(M)、角度しきい値 = 0.1、対数 = 2、データ正規化 = なし、

!!! note
    埋め込みプロセス内のポイント数を最大化するために、このアルゴリズムはN-max(m * tau)遅延ベクトルを使用し、[1][2]で採用されているN-max(m) * max(tau)ではありません。


---

```
MCoSi, Bm = MvCoSiEn(Data::AbstractArray{T,2} where T<:Real; m::Union{AbstractArray{T} where T<:Int, Nothing}=nothing, tau::Union{AbstractArray{T} where T<:Int, Nothing}=nothing, r::Real=.1, Logx::Real=2, Norm::Int=0)
```

指定されたキーワード引数を使用して、`Data`内のM個の多変量データシーケンスから推定された多変量コサイン類似度エントロピー推定値（`MSamp`）を返します：

# 引数：

`Data`    - 多変量データセット、N (>10) の観測（行）とM（列）の単変量データシーケンスのNxM行列

`m`       - 埋め込み次元、M個の正の整数のベクトル

`tau`     - 時間遅延、M個の正の整数のベクトル

`r`     - 角度しきい値、範囲 [0 < r < 1] の値   

`Logx`    - 対数の底、正のスカラー（自然対数の場合は0を入力）

`Norm`    - `Data`の正規化、次の整数のいずれか：

```
        *  [0]  正規化なし - デフォルト
        *  [1]  中央値(`Data`)を除去してゼロ中央値系列を取得
        *  [2]  平均(`Data`)を除去してゼロ平均系列を取得
        *  [3]  `Data`内の各シーケンスを単位分散およびゼロ平均に正規化
        *  [4]  `Data`内の各シーケンスの値を範囲[-1 1]に正規化
```

# 参照： `CoSiEn`, `MvDispEn`, `MvSampEn`, `MvFuzzEn`, `MvPermEn`, `MSEn`

# 参考文献：

```
[1] H. Xiao, T. Chanwimalueang and D. P. Mandic, 
    "Multivariate Multiscale Cosine Similarity Entropy" 
    IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP),
    pp. 5997-6001, doi: 10.1109/ICASSP43922.2022.9747282.

[2] Xiao, H.; Chanwimalueang, T.; Mandic, D.P., 
    "Multivariate Multiscale Cosine Similarity Entropy and Its 
    Application to Examine Circularity Properties in Division Algebras."
    Entropy 2022, 24, 1287. 

[3] Ahmed Mosabber Uddin, Danilo P. Mandic
    "Multivariate multiscale entropy: A tool for complexity
    analysis of multichannel data."
    Physical Review E 84.6 (2011): 061918.

[4] Theerasak Chanwimalueang and Danilo Mandic,
    "Cosine similarity entropy: Self-correlation-based complexity
    analysis of dynamical systems."
    Entropy 
    19.12 (2017): 652.
```
