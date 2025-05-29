```
getfat(file, arclen=10, typlen=10)
```

SPICEカーネルファイルのファイルアーキテクチャとファイルタイプを特定します。

### 引数

  * `file`: 検査するファイルの名前
  * `arclen`: 出力アーキテクチャ文字列の最大長（デフォルト: 10）
  * `typlen`: 出力タイプ文字列の最大長（デフォルト: 10）

### 出力

  * `arch`: カーネルファイルのアーキテクチャ
  * `typ`: カーネルファイルのタイプ

### 参照

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/getfat_c.html)
