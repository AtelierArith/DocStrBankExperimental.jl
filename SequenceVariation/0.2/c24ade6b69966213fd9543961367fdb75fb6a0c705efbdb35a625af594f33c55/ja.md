```
refbases(v::Variation)
```

`v`の参照塩基を取得します。削除の場合、`refbases`は[VCF v4仕様](https://samtools.github.io/hts-specs/VCFv4.3.pdf)の`REF`フィールドに従って、削除の*前*の塩基も返します。
