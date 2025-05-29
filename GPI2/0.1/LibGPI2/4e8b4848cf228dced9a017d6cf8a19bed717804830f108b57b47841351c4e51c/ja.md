```
gaspi_cpu_frequency(cpu_mhz)
```

CPUの周波数を取得します。

### パラメータ

  * `cpu_mhz`: 周波数を格納する出力パラメータ。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERRORを返します。

### プロトタイプ

```c
gaspi_return_t gaspi_cpu_frequency (gaspi_float * const cpu_mhz);
```
