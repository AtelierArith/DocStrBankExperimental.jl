```
Dynamics(dynamics, num_next_state, num_state, num_action;
    num_parameter, checkbounds, constraint_tensor)

dynamics タイプ 

dynamics: 関数 
num_next_state: Int - 次の状態の次元
num_state: Int - 現在の状態の次元 
num_action: Int - 現在のアクションの次元 
num_parameter: Int - 問題データの次元 
checkbounds: Bool - コード生成メソッドの @inbounds チェック用フラグ 
constraint_tensor: Bool - 二次導関数メソッド生成用フラグ
```
