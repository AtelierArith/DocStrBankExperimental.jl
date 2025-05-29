```
inseconds(quantity[, rate])
```

特定の量（通常は時間）を（単位のない）秒の値に変換します。

与えられた量がUnitfulである場合、指定された単位を使用します。そうでない場合は、すでに秒の値であると仮定します。

いくつかの単位（例：フレーム）では、フレームレートを指定する必要があります。指定されていない場合、レートは`missing`です。

## 例

```jldoctest
julia> inseconds(50.0ms)
0.05

julia> inseconds(441frames, 44100Hz)
0.01
```
