```
function fmi3GetVersion(fmu::FMU3)
```

# 引数

  * `c::FMU3Instance`: FMU 3.0 標準におけるインスタンス化された FMU のインスタンスを表す可変構造体。

# 戻り値

  * Cスタイルの（NUL終端）文字列のアドレスから文字列を返します。この文字列は、FMU の関数をコンパイルするために使用された “fmi3Functions.h” ヘッダーファイルのバージョンを表します。この関数は、このヘッダーファイルで定義されている “fmiVersion” を返します。この仕様書に文書化されている標準ヘッダーファイルのバージョンは “3.0” です。

# 出典

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.4. ヘッダーファイルのバージョン番号を照会する
