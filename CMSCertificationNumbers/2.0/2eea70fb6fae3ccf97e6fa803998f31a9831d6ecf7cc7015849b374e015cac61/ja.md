```
EmergencyHospitalCCN
EmergencyHospitalCCN(n::AbstractString)
```

指定された緊急病院プロバイダーを表す型です。

緊急病院プロバイダーは、次の形式の6文字の識別子を使用します：

> `SSQQQE`


ここで：

  * `SS` は2文字の英数字の州コードを表します；
  * `E` はアルファベットの緊急病院タイプコードを表します；
  * `QQQ` は3桁のシーケンス番号を表します。

コンストラクタはエラーチェックを行いませんが、`n` が7文字を超える場合は例外をスローします。
