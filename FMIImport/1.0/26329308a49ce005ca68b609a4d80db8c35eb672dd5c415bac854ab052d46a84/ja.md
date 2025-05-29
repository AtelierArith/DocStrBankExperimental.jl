```
fmi3ExitInitializationMode(c::FMU3Instance)
```

初期化モードを終了するようFMUに通知します。

# 引数

  * `c::FMU3Instance`: 引数 `c` は、FMI 3.0標準におけるFMUのインスタンス化されたインスタンスを表す可変構造体です。

# 戻り値

  * `status::fmi3Status`: 戻り値 `status` は `fmi3Status` 型の列挙体で、関数呼び出しの成功を示します。

より詳細には:     - `fmi3OK`: すべて正常     - `fmi3Warning`: いくつかの問題があるが、計算は続行可能     - `fmi3Discard`: スレーブが通信ステップのサブインターバルのみを正常に計算した場合     - `fmi3Error`: 通信ステップを全く実行できなかった場合     - `fmi3Fatal`: FMUを不可逆的に破損させるエラーが発生した場合

# 出典

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 2.2.4 関数によって返されるステータス
  * FMISpec3.0: 2.3.3. 状態: 初期化モード

さらに [`fmi3ExitInitializationMode`](@ref) を参照してください。
