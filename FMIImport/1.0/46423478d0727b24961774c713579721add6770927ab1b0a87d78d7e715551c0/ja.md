```
fmi2GetTypesPlatform(fmu::FMU2)
```

FMUの関数のコンパイルに使用される「fmi2TypesPlatform.h」ヘッダーファイルを一意に識別するための文字列を返します。この仕様に文書化されている標準ヘッダーファイルでは、fmi2TypesPlatformは「default」に設定されています（したがって、この関数は通常「default」を返します）。

# 引数

  * `fmu::FMU2`: FMI 2.0.2標準におけるFMUとそのすべてのインスタンスを表す可変構造体。

# 戻り値

  * FMUの関数のコンパイルに使用される「fmi2TypesPlatform.h」ヘッダーファイルを一意に識別するための文字列を返します。

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.22]: 2.1.4 ヘッダーファイルのプラットフォームとバージョン番号を照会する
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義
