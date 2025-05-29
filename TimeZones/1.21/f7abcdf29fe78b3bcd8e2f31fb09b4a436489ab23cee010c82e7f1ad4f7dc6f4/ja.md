```
build(version::AbstractString; force::Bool=false) -> Nothing
```

指定された tzdata `version` と `regions` で TimeZones パッケージをビルドします。`version` は通常、4 桁の年の後に小文字の ASCII 文字が続く形式です（例："2025b"）。`force` フラグは tzdata アーカイブを再ダウンロードするために使用されます。

!!! warning
    この関数は *スレッドセーフ* ではなく、主に実験のために意図されています。

