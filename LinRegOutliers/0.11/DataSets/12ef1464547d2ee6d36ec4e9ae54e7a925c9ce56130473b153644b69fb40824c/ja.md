スタックロスデータ

# コンポーネント

  * `airflow::Float64`: 冷却空気の流量（独立変数）。
  * `watertemp::Float64`: 冷却水の入口温度（独立変数）。
  * `acidcond::Float64`: 酸の濃度（独立変数）。
  * `stackloss::Float64`: スタックロス（従属変数）。

# 外れ値

```
観測値1、3、4、および21は外れ値です。
```

# 参考文献

```
Becker, R. A., Chambers, J. M. and Wilks, A. R. (1988) _The New S Language_.  Wadsworth & Brooks/Cole.

Dodge, Y. (1996) The guinea pig of multiple regression. In: _Robust Statistics, Data Analysis, and Computer Intensive Methods;
In Honor of Peter Huber's 60th Birthday_, 1996, _Lecture Notes in Statistics_ *109*, Springer-Verlag, New York.
```
