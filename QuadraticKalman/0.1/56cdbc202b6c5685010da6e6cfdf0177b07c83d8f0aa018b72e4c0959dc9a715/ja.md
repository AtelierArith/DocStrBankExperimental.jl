```
QKModel(state::StateParams, meas::MeasParams; check_stability::Bool=false)
```

QKModelの代替コンストラクタで、事前に構築された状態および測定パラメータオブジェクトを受け取ります。

# 引数

  * `state::StateParams`: N、mu、Phi、およびOmegaを含む状態パラメータオブジェクト
  * `meas::MeasParams`: M、A、B、C、D、およびalphaを含む測定パラメータオブジェクト

# キーワード引数

  * `check_stability::Bool=false`: trueの場合、状態遷移ダイナミクスが安定しているかどうかをチェックします

# 戻り値

パラメータを展開して主コンストラクタを呼び出すことによってQKModelオブジェクトを返します。

# 例

```julia
# パラメータオブジェクトを作成
state = StateParams(2, [0.0, 0.0], [0.9 0.0; 0.0 0.9], [0.1 0.0; 0.0 0.1])
meas = MeasParams(1, 2, [0.0], [1.0 1.0], [reshape([1.0 0.0; 0.0 1.0], 2, 2)], [0.1], [0.0])

# モデルを作成
model = QKModel(state, meas)
```

参照: `QKModel`, `StateParams`, `MeasParams`
