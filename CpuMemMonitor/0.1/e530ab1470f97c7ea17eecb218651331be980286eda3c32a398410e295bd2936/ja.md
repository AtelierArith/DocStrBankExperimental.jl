```
function start_monitor(
    pid::Int64,
    fn::String; # 情報を保存するために使用されるファイル名
    iterations::Int64 = 8,
    interval::Int64 = 1,
    outer_interval::Int64 = 3600
)

CPUとMEMの情報をそれぞれ2つのファイルに保存します。
```
