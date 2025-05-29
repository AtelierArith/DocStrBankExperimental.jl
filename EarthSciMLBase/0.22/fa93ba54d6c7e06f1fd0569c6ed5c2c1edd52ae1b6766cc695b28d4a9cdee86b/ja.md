暗黙的-明示的 (IMEX) 時間統合に基づくソルバ戦略。詳細については[こちら](https://docs.sciml.ai/DiffEqDocs/stable/types/split_ode_types/)を参照してください。

kwargs:

  * stiff_sparse: 硬いODE関数がスパースヤコビアンを使用するかどうか。
  * stiff_tgrad: 硬いODE関数が解析的時間勾配を使用するかどうか。

ODEProblemコンストラクタの追加kwargs:

  * u0: 初期条件; "nothing"の場合、デフォルト値が使用されます。
  * p: パラメータ; "nothing"の場合、デフォルト値が使用されます。
  * name: モデルの名前。
