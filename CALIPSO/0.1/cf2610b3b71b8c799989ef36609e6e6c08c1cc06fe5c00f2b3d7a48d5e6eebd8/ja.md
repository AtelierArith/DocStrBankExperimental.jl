```
Constraint(constraint, num_state, num_action;
    num_parameter, checkbounds, constraint_tensor)

constraint type 

constraint: Function 
num_state: Int - 状態の次元 
num_action: Int - 行動の次元 
num_parameter: Int - 問題データの次元 
checkbounds: Bool - コード生成メソッドのための@inboundsチェックフラグ 
constraint_tensor: Bool - 二次導関数メソッド生成のためのフラグ
```
