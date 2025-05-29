```
  Spec, BandEn = SpecEn(Sig)
```

フルスペクトルのスペクトルエントロピー推定値（`Spec`）と、データシーケンス（`Sig`）から推定されたバンド内エントロピー（`BandEn`）を返します。デフォルトのパラメータを使用します：NポイントFFT = 2*len（`Sig`） + 1、正規化されたバンドエッジ周波数 = [0 1]、対数 = 基数2、正規化 = スペクトル/バンド周波数値の数に関して。

```
  Spec, BandEn = SpecEn(Sig::AbstractArray{T,1} where T<:Real; N::Int=1 + (2*size(Sig,1)), Freqs::Tuple{Real,Real}=(0,1), Logx::Real=exp(1), Norm::Bool=true)
```

指定された「キーワード」引数を使用して、データシーケンス（`Sig`）のスペクトルエントロピー（`Spec`）とバンド内エントロピー（`BandEn`）の推定値を返します。

# 引数：

`N`     - スペクトルの解像度（NポイントFFT）、1より大きい整数  

`Freqs` - 正規化されたバンドエッジ周波数、値を持つ2要素のタプル 

```
        範囲[0 1]内で、1はナイキスト周波数（Fs/2）に対応します。
        注意：バンド周波数が入力されていない場合、BandEn == SpecEn
```

`Logx`  - 対数の基数、正のスカラー（自然対数の場合は0を入力） 

`Norm`  - `Spec`値の正規化：

```
        [false]  正規化なし。
        [true]   スペクトル/バンド周波数値の数に関して正規化 - デフォルト。
```

詳細については、EntropyHubガイドを参照してください。

# 参照：`XSpecEn`、`fft`、`MSEn`、`XMSEn`

# 参考文献：

```
  [1] G.E. Powell and I.C. Percival,
      "A spectral entropy method for distinguishing regular and 
      irregular motion of Hamiltonian systems." 
      Journal of Physics A: Mathematical and General 
      12.11 (1979): 2053.

  [2] Tsuyoshi Inouye, et al.,
      "Quantification of EEG irregularity by use of the entropy of 
      the power spectrum." 
      Electroencephalography and clinical neurophysiology 
      79.3 (1991): 204-210.
```
