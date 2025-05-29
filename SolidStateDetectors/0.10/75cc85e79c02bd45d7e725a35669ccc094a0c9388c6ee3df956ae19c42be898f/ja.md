```
add_baseline_and_extend_tail(wv::RadiationDetectorSignals.RDWaveform{T,U,TV,UV}, n_baseline_samples::Int, total_waveform_length::Int) where {T,U,TV,UV}
```

波形 `wv` の前にゼロ値のベースラインを追加し、波形の最後を `wv` の最後の値で延長（またはカットオフ）します。長さ `total_waveform_length` の波形が返されます。

## 引数

  * `wv::RadiationDetectorSignals.RDWaveform{T,U,TV,UV}`: 波形（時間に対する信号）。
  * `n_baseline_samples::Int`: 波形の前に追加されるゼロ値のサンプル数。
  * `total_waveform_length::Int`: 返される拡張波形のサンプル数。

## 例

```
add_baseline_and_extend_tail(wv, 1000, 5000)
```

!!! note
    この関数は、入力波形 `wv` のサンプル間の時間ステップが同じであると仮定しています。したがって、入力波形は固定周波数でサンプリングされています。

