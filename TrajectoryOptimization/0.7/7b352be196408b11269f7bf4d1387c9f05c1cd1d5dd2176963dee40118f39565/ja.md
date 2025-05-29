```
LinearConstraint{S,P,W,T}
```

形式 $Ay - b \{\leq,=\} 0$ の線形制約で、$y$ は状態または制御のいずれかである（ただし、両方の組み合わせではない）。

# コンストラクタ: ```julia

LinearConstraint{S,W}(n,m,A,b) ```where`W <: Union{State,Control}`.
