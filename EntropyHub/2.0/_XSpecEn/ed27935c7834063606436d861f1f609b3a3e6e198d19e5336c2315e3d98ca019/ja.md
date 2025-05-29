```
   XSpec, BandEn = XSpecEn(Sig)
```

フルクロススペクトルのクロススペクトルエントロピー推定値（`XSpec`）と、`Sig`に含まれるデータシーケンス間で推定されたバンド内エントロピー（`BandEn`）を返します。デフォルトのパラメータを使用します：NポイントFFT = 2 * max(length(`Sig1`/`Sig2`)) + 1、正規化されたバンドエッジ周波数 = [0 1]、対数 = 基数2、正規化 = スペクトル/バンド周波数値の数に対して。

```
   XSpec, BandEn = XSpecEn(Sig1::Union{AbstractMatrix{T}, AbstractVector{T}} where T<:Real, Sig2::Union{AbstractVector{T} where T<:Real, Nothing} = nothing;  N::Union{Nothing,Int}=nothing, Freqs::Tuple{Real,Real}=(0,1), Logx::Real=exp(1), Norm::Bool=true)
```

`Sig1`と`Sig2`に含まれるデータシーケンス間のクロススペクトルエントロピー（`XSpec`）とバンド内エントロピー（`BandEn`）の推定値を、以下の指定された「キーワード」引数を使用して返します：

# 引数：

`N`     - スペクトルの解像度（NポイントFFT）、1より大きい整数    

`Freqs` - 正規化されたバンドエッジ周波数、スカラーで範囲は[0 1]              1はナイキスト周波数（Fs/2）に対応します。              **注意：バンド周波数が入力されていない場合、BandEn == SpecEn** 

`Logx`  - 対数の基数、正のスカラー     [デフォルト：基数2]              **自然対数の場合は0を入力**  

`Norm`  - `XSpec`値の正規化：              [false]  正規化なし。              [true]   スペクトル/バンド周波数値の数に対して正規化 [デフォルト] 

詳細については、EntropyHubガイドを参照してください。

# 参照： `SpecEn`, `fft`, `XDistEn`, `periodogram`, `XSampEn`, `XApEn`

# 参考文献：

```
   [1]  Matthew W. Flood,
       "XSpecEn - EntropyHub Project"
       (2021) https://github.com/MattWillFlood/EntropyHub
```
