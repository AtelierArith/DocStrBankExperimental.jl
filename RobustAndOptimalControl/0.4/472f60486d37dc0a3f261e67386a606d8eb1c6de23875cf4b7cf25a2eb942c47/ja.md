```
extended_controller(l::LQGProblem, L = lqr(l), K = kalman(l); z = nothing)
```

状態フィードバック `u = L(xᵣ-x̂)` と状態推定値 x̂ を生成するゲイン `K` を持つカルマンフィルタを組み合わせたときに得られるコントローラを表す状態空間システムを返します。コントローラは `ExtendedStateSpace` のインスタンスであり、`C2 = -L, D21 = L` および `B2 = K` です。

返されるシステムは *入力* `[xᵣ; y]` を持ち、制御信号 `u` を出力します。参照モデル `R` が状態参照 `xᵣ` を生成するために使用される場合、`(ry, y) -> u` から得られるコントローラは、`ry - y = e` で与えられます。

```julia
Ce = extended_controller(l)
Ce = named_ss(ss(Ce); x = :xC, y = :u, u = [R.y; :y^l.ny]) # Ce の入力を `R` の出力と同じ名前にします。
connect([R, Ce]; u1 = R.y, y1 = R.y, w1 = [R.u; :y^l.ny], z1=[:u])
```

フィードバックの負の部分が返されるシステムに組み込まれているため、次のようになります。

```julia
C = observer_controller(l)
Ce = extended_controller(l)
system_mapping(Ce) == -C
```

参照前フィルタがない場合、参照から制御出力へのDCゲインは単位でない可能性があることに注意してください。キーワード引数 `z` を通じて出力インデックスのベクトルが提供されると、状態参照 `xᵣ` から出力 `z` への閉ループシステムが2番目の戻り値として返されます。この閉ループシステムのDCゲインの逆数は、コントローラのDCゲインを補償するのに役立つかもしれません。 ```
