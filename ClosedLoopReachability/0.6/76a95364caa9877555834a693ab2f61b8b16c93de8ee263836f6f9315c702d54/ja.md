```
ControlledPlant{ST, CT, XT, DT, PT, CPRT, CPST} <: AbstractControlProblem
```

閉ループ制御システムを表す構造体。

### フィールド

  * `ivp`            – 初期値問題
  * `controller`     – コントローラ
  * `vars`           – 状態変数、入力変数、制御変数を格納する辞書
  * `period`         – 制御周期
  * `postprocessing` – コントローラ出力の後処理
  * `preprocessing`  – コントローラ入力の前処理

### パラメータ

  * `ST`:  システムのタイプ
  * `CT`:  コントローラのタイプ
  * `XT`:  初期条件のタイプ
  * `DT`:  変数のタイプ
  * `PT`:  周期のタイプ
  * `CPRT`: 制御前処理のタイプ
  * `CPST`: 制御後処理のタイプ

### 注意事項

通常、`controller`はニューラルネットワークですが、この構造体はタイプを指定しません。
