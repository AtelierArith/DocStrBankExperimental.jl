```
MPerm, MPnorm = MvPermEn(Data)
```

多変量順列エントロピー推定値（`MPerm`）と、デフォルトパラメータを使用して`Data`内のM個の多変量系列の正規化順列エントロピーを返します：埋め込み次元 = 2*ones(M,1)、時間遅延 = ones(M,1)、対数 = 2、正規化 = シンボル数に対して（sum(`m-1`））

!!! note
    ここで実装されている多変量順列エントロピーアルゴリズムは、タケンズの埋め込み定理に基づく多変量埋め込みを使用し、アフメドとマンディックによって元々提示された共有空間再構成を通じた多変量エントロピー推定の方法に従います[1]。

    この関数は、個々の単変量系列のエントロピー値を平均化するモラビトらの多変量順列エントロピーアルゴリズム（Entropy, 2012）を**使用しません**。なぜなら、そのような方法は多変量埋め込みの定義に従わず、したがってクロスチャネルの統計的複雑さを考慮しないからです。

    埋め込みプロセスにおけるポイント数を最大化するために、このアルゴリズムはN-max(tau * m)遅延ベクトルを使用し、[1]で採用されているN-max(m) * max(tau)ではありません。


---

```
MPerm, MPnorm = MvPermEn(Data::AbstractArray{T} where T<:Real; m::Union{AbstractArray{T} where T<:Int, Nothing}=nothing, tau::Union{AbstractArray{T} where T<:Int, Nothing}=nothing, Typex::String="none", tpx::Union{Int,Nothing}=nothing, Norm::Bool=false, Logx::Real=2)
```

指定されたキーワード引数を使用して、`Data`内のM個の多変量データ系列に対する多変量順列エントロピー推定値（`MPerm`）を返します：

# 引数：

`Data`  - 多変量データセット、N (>10)の観測（行）とM（列）の単変量データ系列のNxM行列

`m`     - 埋め込み次元、M個の正の整数のベクトル

`tau`   - 時間遅延、M個の正の整数のベクトル

`Typex` - 順列エントロピーのバリエーション、次の文字列のいずれか：

```
        {`'modified'`, `'ampaware'`, `'weighted'`, `'edge'`, `'phase'`}
        MvPermEnのバリエーションに関する詳細は、`EntropyHubガイド <https://github.com/MattWillFlood/EntropyHub/blob/main/EntropyHub%20Guide.pdf>`_を参照してください。
```

`tpx`   - 関連する順列エントロピーのバリエーションの調整パラメータ。

```
        *   [ampaware]  `tpx`はAパラメータで、範囲[0 1]の値；デフォルト = 0.5
        *   [edge]      `tpx`はr感度パラメータで、スカラー> 0；デフォルト = 1
        *   [phase]     `tpx`はヒルベルト変換信号の位相角をアンラップするオプションで、[]または1（デフォルト = 0）
```

`Norm`  - MPnorm値の正規化、ブール演算子：

```
        *   false -  順列シンボルの数に対するlog（[sum(m)-1]）で正規化 - デフォルト
        *   true  -  すべての可能な順列の数に対するlog（[sum(m)!]）で正規化
```

`Logx`   - 対数の底、正のスカラー 

# 参照    `PermEn`, `PermEn2D`, `XPermEn`, `MSEn`, `MvFuzzEn`, `MvSampEn`

# 参考文献：

```
[1] Ahmed Mosabber Uddin, Danilo P. Mandic
    "Multivariate multiscale entropy: A tool for complexity
    analysis of multichannel data."
    Physical Review E 84.6 (2011): 061918.

[2] Christoph Bandt and Bernd Pompe, 
    "Permutation entropy: A natural complexity measure for time series." 
    Physical Review Letters,
    88.17 (2002): 174102.

[3] Chunhua Bian, et al.,
    "Modified permutation-entropy analysis of heartbeat dynamics."
    Physical Review E
    85.2 (2012) : 021906

[4] Bilal Fadlallah, et al.,
    "Weighted-permutation entropy: A complexity measure for time 
    series incorporating amplitude information." 
    Physical Review E 
    87.2 (2013): 022911.

[5] Hamed Azami and Javier Escudero,
    "Amplitude-aware permutation entropy: Illustration in spike 
    detection and signal segmentation." 
    Computer methods and programs in biomedicine,
    128 (2016): 40-51.

[6] Zhiqiang Huo, et al.,
    "Edge Permutation Entropy: An Improved Entropy Measure for 
    Time-Series Analysis," 
    45th Annual Conference of the IEEE Industrial Electronics Soc,
    (2019), 5998-6003

[7] Maik Riedl, Andreas Müller, and Niels Wessel,
    "Practical considerations of permutation entropy." 
    The European Physical Journal Special Topics 
    222.2 (2013): 249-262.

[8] Kang Huan, Xiaofeng Zhang, and Guangbin Zhang,
    "Phase permutation entropy: A complexity measure for nonlinear time
    series incorporating phase information."
    Physica A: Statistical Mechanics and its Applications
    568 (2021): 125686.
```
