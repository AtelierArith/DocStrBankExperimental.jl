```
specific_humidity_from_dewpoint(dewpoint_temperature, temperature, air_pressure, earth_param_set)
```

露点温度、ケルビンでの空気温度、パスカルでの気圧、および ClimaLand earth*param*set を考慮して、特定の湿度を推定します。これは、ERA5 再解析データから特定の湿度が必要な PrescribedAtmosphere を作成するのに役立ちます。

まず、マグヌスの公式を使用して相対湿度を計算し、次に飽和水蒸気圧を計算し、最後に水蒸気圧と飽和水蒸気圧から q を計算します。

マグヌスの公式に関する詳細については、例えば、Lawrence, Mark G. (2005年2月1日) の「湿った空気における相対湿度と露点温度の関係：簡単な変換と応用」を参照してください。アメリカ気象学会のブレティン。86 (2): 225–234.
