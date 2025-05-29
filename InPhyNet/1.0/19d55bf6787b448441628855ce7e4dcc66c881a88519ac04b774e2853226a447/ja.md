```
calculateAGIC(Ns::AbstractVector{HybridNetwork})
```

すべてのネットワークにわたるすべてのタクソンのペアに対して、**A**verage **G**ene tree **I**nternode **C**ountsを計算します。`allow_missing_pairs`がfalseの場合、`Ns`に一緒に現れないタクソンのペアがあるとエラーが発生します。それ以外の場合、一緒に現れないタクソンのエントリは`default_missing_value`に設定されます。

# 戻り値

1. AGIC行列
2. AGID行列の行/列に対応するタクソンの名前
