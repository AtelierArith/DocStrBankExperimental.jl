```
comp = get_adc_phase_compensation(seq)
```

位相補償因子の配列 $\exp(-\mathrm{i}\varphi)$ を返します。これは、シミュレーション後に操作 $S_{\mathrm{comp}} = S \exp(-\mathrm{i}\varphi)$ を適用することによって取得した信号 $S$ を補償するために使用されます。この補償は、信号が通常、位相 $\varphi$ の RF 励起に続いて位相オフセット $\varphi$ を示すため、必要です。このようなパルスは、RF スポイリングを含むシーケンスで一般的に使用されます。

# 引数

  * `seq`: (`::Sequence`) シーケンス構造体

# 戻り値

  * `comp`: (`::Vector{Complex}`, `[rad]`) 取得した各サンプルの位相補償の配列

```
