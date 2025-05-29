軽量なJuliaラッパーである[WORLD](https://github.com/mmorise/World)は、高品質な音声分析、操作、合成システムです。WORLDは、音声信号を以下のように分解する方法を提供します：

  * 基本周波数 (F0)
  * スペクトルエンベロープ
  * 非周期性

これらのパラメータから音声信号を再合成します。WORLDの詳細については、プロジェクトページをご覧ください。

!!! note
    WORLD.jlは、WORLDのフォークである[r9y9/World-cmake](https://github.com/r9y9/World-cmake)に基づいています。


[https://github.com/r9y9/WORLD.jl](https://github.com/r9y9/WORLD.jl)

## 使用法

以下の例では、`x::Vector{Float64}`が入力モノラル音声信号であるとします：

![](assets/x.png)

### F0推定

#### Harvest

```julia
opt = HarvestOption(71.0, 800.0, period)
f0, timeaxis = harvest(x, fs, opt)
```

![](assets/f0_by_harvest.png)

#### Dio

```julia
opt = DioOption(f0floor=71.0, f0ceil=800.0, channels_in_octave=2.0,
        period=period, speed=1)
f0, timeaxis = dio(x, fs, opt)
```

![](assets/f0_by_dio.png)

#### StoneMask

```julia
f0 = stonemask(x, fs, timeaxis, f0)
```

![](assets/f0_refinement.png)

### CheapTrickによるスペクトルエンベロープ推定

```julia
spectrogram = cheaptrick(x, fs, timeaxis, f0)
```

![](assets/envelope_by_cheaptrick.png)

### D4Cによる非周期性比率推定

```julia
aperiodicity = d4c(x, fs, timeaxis, f0)
```

![](assets/aperiodicity_by_d4c.png)

### 合成

```julia
y = synthesis(f0, spectrogram, aperiodicity, period, fs, length(x))
```

![](assets/synthesis.png)

### コンパクトな音声パラメータ化

生のスペクトラムエンベロープと非周期性スペクトラムは比較的高次元（しばしば513または1025を超える）であるため、よりコンパクトな表現を得たい場合があります。この状況に対処するために、WORLDはスペクトラムエンベロープと非周期性のコーディング/デコーディングAPIを提供します。さらに、WORLD.jlはスペクトラムエンベロープからメルケプストラムへの変換とその逆も提供します。目的に応じて、任意のコーディング/デコーディングAPIを選択できます。

#### スペクトラムエンベロープからメルケプストラムへ

```julia
mc = sp2mc(spectrogram, order, α) # 例：order=40, α=0.41
```

ここで、`order`はメルケプストラムの次数（0次を除く）で、αは周波数ワーピングパラメータです。

![](assets/melcepstrum.png)

#### メルケプストラムからスペクトラムエンベロープへ

```julia
approximate_spectrogram = mc2sp(mc, α, get_fftsize_for_cheaptrick(fs))
```

![](assets/envelope_reconstructed_from_melcepstrum.png)

#### 非周期性のコーディング

```julia
coded_aperiodicity = code_aperiodicity(aperiodicity, fs)
```

![](assets/coded_aperiodicity.png)

#### 非周期性のデコーディング

```julia
decoded_aperiodicity = decode_aperiodicity(coded_aperiodicity, fs)
```

![](assets/decoded_aperiodicity.png)

上記の視覚化に関する完全なコードについては、[IJuliaノートブック](http://nbviewer.jupyter.org/github/r9y9/WORLD.jl/blob/master/docs/src/assets/WORLD-demo.ipynb)を確認してください。

## エクスポート

  * [`CheapTrickOption`](@ref)
  * [`D4COption`](@ref)
  * [`DioOption`](@ref)
  * [`HarvestOption`](@ref)
  * [`cheaptrick`](@ref)
  * [`code_aperiodicity`](@ref)
  * [`code_spectral_envelope`](@ref)
  * [`d4c`](@ref)
  * [`decode_aperiodicity`](@ref)
  * [`decode_spectral_envelope`](@ref)
  * [`dio`](@ref)
  * [`get_fftsize_for_cheaptrick`](@ref)
  * [`get_number_of_aperiodicities`](@ref)
  * [`harvest`](@ref)
  * [`interp1`](@ref)
  * [`interp1!`](@ref)
  * [`mc2sp`](@ref)
  * [`sp2mc`](@ref)
  * [`stonemask`](@ref)
  * [`synthesis`](@ref)
