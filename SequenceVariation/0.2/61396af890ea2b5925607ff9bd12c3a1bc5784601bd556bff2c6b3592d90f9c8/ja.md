```
altbases(v::Variation)
```

`v`の代替塩基を取得します。挿入の場合、`altbases`は挿入の前の塩基も返します。これは[VCF v4仕様](https://samtools.github.io/hts-specs/VCFv4.3.pdf)の`ALT`フィールドに従っています。
