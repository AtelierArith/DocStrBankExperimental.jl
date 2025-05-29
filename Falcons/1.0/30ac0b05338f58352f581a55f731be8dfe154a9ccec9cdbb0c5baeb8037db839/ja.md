```
get_pointing_pixels(ss::ScanningStrategy, start, stop)
```

この関数は、トッドの指向ピクセルをタプルとして返します。     # 引数     ...     - `ss::ScanningStrategy`: ScanningStrategy 構造体。     - `start::Int`: 指向計算の初期時間。     - `stop::Int`: 指向計算の終了時間。     ...

````
# 例
```jldoctest
julia> ss = gen_ScanningStrategy()
julia> pointings = get_pointing_pixels(s, 0, 100)

# 戻り値
...
- `pointings[1]`: ピクセルインデックスの TOD。形状:(duration*sampling_rate, numOfdet)
- `pointings[2]`: psi の TOD。形状:(duration*sampling_rate, numOfdet)
- `pointings[3]`: 時間の配列。形状:(duration*sampling_rate)
...
````
