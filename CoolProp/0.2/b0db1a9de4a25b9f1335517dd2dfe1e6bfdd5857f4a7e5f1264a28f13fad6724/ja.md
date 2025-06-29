```
set_config(key::AbstractString, val::Real)
```

設定の数値を倍精度として設定します。

# 引数

  * `key::AbstractString`: 設定するキー。以下の表に可能な `key` の値、そのデフォルト設定、およびその使用法を示します。
  * `val::Real`: キーに設定する値

| キー                                  |   デフォルト   | 説明                                                                                    |
|:----------------------------------- |:---------:|:------------------------------------------------------------------------------------- |
| MAXIMUM*TABLE*DIRECTORY*SIZE*IN_GB  |    1.0    | 表形式データを保存するために使用されるディレクトリの最大許可サイズ                                                     |
| PHASE*ENVELOPE*STARTING*PRESSURE*PA |   100.0   | フェーズエンベロープ構築のための開始圧力 [Pa]                                                             |
| R*U*CODATA                          | 8.3144598 | CODATA 2014 によるモルあたりの理想気体定数の値 (J/mol/K)。この値はすべての理想気体定数を調和させるために使用されます。これは特に臨界領域で重要です。 |
| SPINODAL*MINIMUM*DELTA              |    0.5    | スピノダルを追跡するために使用される最小デルタ; EOS がこのデルタの値でスピノダルを持つことを確認してください (delta=rho/rho_r)           |
