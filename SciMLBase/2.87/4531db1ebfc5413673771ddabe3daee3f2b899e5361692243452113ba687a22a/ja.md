```
reeval_internals_due_to_modification!(integrator::DEIntegrator, continuous_modification::Bool=true;
                                      callback_initializealg = nothing)
```

コールバックによる変更後にDEインテグレーターを更新します。DAE（暗黙的または半明示的のいずれか）の場合、これは代数変数の再解決を必要とします。continuous_modificationがtrue（または未指定）の場合、これは補間データの再計算も行う必要があります。そうでない場合、インテグレーターは補間の再計算をスキップすることが許可されます。

# 引数

  * `continuous_modification`: 変更が連続的な変化（連続コールバック）によるものか、離散的なコールバックによるものかを決定します。連続的な変化の場合、これは再評価を必要とする時間の変更を含むことがあります。
  * `callback_initializealg`: コールバックによって提供される初期化アルゴリズム。DAEの場合、これはコールバック後に行われる初期化の選択です。デフォルト値の`nothing`は、DAEに対して使用される初期化の選択がコールバック後に行われるべきであることを意味します。
