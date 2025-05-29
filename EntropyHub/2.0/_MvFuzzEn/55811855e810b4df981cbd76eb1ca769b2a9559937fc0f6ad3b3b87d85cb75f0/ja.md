```
MFuzz, B0, Bt, B1 = MvFuzzEn(Data)
```

`MFuzz`（多変量ファジーエントロピー推定値）と平均ベクトル距離（`m`：`B0`；結合総和 `m+1` サブスペース：`Bt`；すべての可能な `m+1` サブスペース：`B1`）を、デフォルトのパラメータを使用して `Data` 内の M 個の多変量シーケンスから返します：埋め込み次元 = 2*ones(M,1)、時間遅延 = ones(M,1)、ファジー会員関数 = "default"、ファジー関数パラメータ = [0.2, 2]、対数 = 自然、データ正規化 = false、

!!! note
    `MFuzz` として返されるエントロピー値は、"full" メソッド [すなわち -log(Bt/B0)] を使用して推定され、これは [1][3] で適用される埋め込み空間のすべての可能な `m+1` 拡張にわたって遅延ベクトルを比較します。従来のサンプルエントロピーの定義とは異なり、この方法は 0 の下限を提供しません!! したがって、確率過程に対しても多変量ファジーエントロピーの負のエントロピー値を取得することが可能です...

    代わりに、個々の `m+1` サブスペース (B1) の平均ベクトル距離を使用して `MFuzz` を "naive" メソッドで計算することができ、これにより 0 の下限が保証されます [例：-log(B1(1)/B0)]、またはすべての `m+1` サブスペースの平均 [すなわち -log(mean(B1)/B0)]。

    埋め込みプロセスのポイント数を最大化するために、このアルゴリズムは N - max(m * tau) 遅延ベクトルを使用し、**N - max(m) * max(tau)** は [1] および [3] で使用されるものではありません。


---

```
MFuzz, B0, Bt, B1 = MvFuzzEn(Data::AbstractArray{T} where T<:Real; m::Union{AbstractArray{T} where T<:Int, Nothing}=nothing, tau::Union{AbstractArray{T} where T<:Int, Nothing}=nothing, r::Union{Real,Tuple{Real,Real}}=(.2,2.0), Fx::String="default", Logx::Real=exp(1), Norm::Bool=false)
```

`Data` 内の M 個の多変量データシーケンスから指定されたキーワード引数を使用して推定された多変量サンプルエントロピー推定値 (`MSamp`) を返します：

# 引数：

`Data`  - 多変量データセット、N (>10) 観測（行）と M（列）単変量データシーケンスの NxM 行列

`m`     - 埋め込み次元、M 個の正の整数のベクトル

`tau`   - 時間遅延、M 個の正の整数のベクトル

`Fx`    - ファジー関数名、次のいずれか：              {`"sigmoid", "modsampen", "default", "gudermannian",`             `"bell", "triangular", "trapezoidal1", "trapezoidal2",`             `"z_shaped", "gaussian", "constgaussian"`}

`r`      - ファジー関数パラメータ、1 要素のスカラーまたは正の値の 2 要素のタプル。各ファジー関数の `r` パラメータは次のように定義されます：      [デフォルト: [.2 2]]

```
            default:        r(1) = 指数引数の除数
                            r(2) = 引数の指数（前除算）
            sigmoid:        r(1) = 指数引数の除数
                            r(2) = 引数から引かれる値（前除算）
            modsampen:      r(1) = 指数引数の除数
                            r(2) = 引数から引かれる値（前除算）
            gudermannian:   r  = スカラーで、その値は gudermannian 関数への引数の分子：
                                GD(x) = atan(tanh(`r`/x))
            triangular:     r = スカラーで、その値は三角関数の閾値（コーナーポイント）。
            trapezoidal1:   r = スカラーで、その値は台形の上部 (2r) および下部 (r) コーナーポイントに対応します。
            trapezoidal2:   r(1) = 台形の上部コーナーポイントに対応する値。
                            r(2) = 台形の下部コーナーポイントに対応する値。
            z_shaped:       r = スカラーで、その値は z 形の上部 (2r) および下部 (r) コーナーポイントに対応します。
            bell:           r(1) = 距離値の除数
                            r(2) = 一般化されたベル型関数の指数
            gaussian:       r = スカラーで、その値はガウス曲線の傾きをスケーリングします。
            constgaussian:  r = スカラーで、その値はガウス曲線の下限閾値と形状を定義します。
```

`Logx`   - 対数の底、正のスカラー 

`Norm`   - すべての M シーケンスを単位分散に正規化するかどうか、ブール値

# 参照： `MvSampEn`, `FuzzEn`, `XFuzzEn`, `FuzzEn2D`, `MSEn`, `MvPermEn`

# 参考文献：

```
[1] Ahmed, Mosabber U., et al. 
    "A multivariate multiscale fuzzy entropy algorithm with application
    to uterine EMG complexity analysis." 
    Entropy 19.1 (2016): 2.

[2] Azami, Alberto Fernández, Javier Escudero. 
    "Refined multiscale fuzzy entropy based on standard deviation for 
    biomedical signal analysis." 
    Medical & biological engineering & computing 55 (2017): 2037-2052.

[3] Ahmed Mosabber Uddin, Danilo P. Mandic
    "Multivariate multiscale entropy analysis."
    IEEE signal processing letters 19.2 (2011): 91-94.
```
