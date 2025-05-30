```
PINNAttention(H_net, U_net, V_net, fusion_layers)
PINNAttention(in_dims::Int, out_dims::Int, activation::Function=sin;
              hidden_dims::Int, num_layers::Int)
```

`H_net`の出力次元と`fusion_layers`の入力次元は同じでなければなりません。2番目と3番目のコンストラクタでは、`H_net`、`U_net`、および`V_net`に`Dense`レイヤーが使用されます。最初のコンストラクタには出力レイヤーが**含まれていない**ことに注意してくださいが、2番目のものには含まれています。

```
                 x → U_net → u                           u
                               ↘                           ↘
x → H_net →  h1 → fusionlayer1 → connection → fusionlayer2 → connection
                               ↗                           ↗
                 x → V_net → v                           v
```

## 引数

  * `H_net`: `AbstractExplicitLayer`。
  * `U_net`: `AbstractExplicitLayer`。
  * `V_net`: `AbstractExplicitLayer`。
  * `fusion_layers`: `Chain`。

## キーワード引数

  * `num_layers`: 隠れ層の数。
  * `hidden_dims`: 各隠れ層の隠れ次元の数。

## 参考文献

[wang2021understanding](@cite)
