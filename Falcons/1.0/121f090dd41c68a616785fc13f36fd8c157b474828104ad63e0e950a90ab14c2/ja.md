```
get_pointings_tuple(ss::ScanningStrategy_ThetaPhi, start, stop)
```

この関数は、ポイントをタプルとして返します。     # 引数     ...     - `ss::ScanningStrategy_ThetaPhi`: ScanningStrategy_ThetaPhi 構造体。     - `start::Int`: ポイント計算の初期時間。     - `stop::Int`: ポイント計算の終了時間。     ...

````
# 例
```jldoctest
julia> ss = gen_ScanningStrategy_ThetaPhi()
julia> pointings = get_pointings_tuple(s, 0, 100)

# 戻り値
...
- `pointings[1]`: θのTOD。形状:(duration*sampling_rate, numOfdet)
- `pointings[2]`: φのTOD。形状:(duration*sampling_rate, numOfdet)
- `pointings[3]`: ψのTOD。形状:(duration*sampling_rate, numOfdet)
- `pointings[4]`: 時間の配列。形状:(duration*sampling_rate)
...
````
