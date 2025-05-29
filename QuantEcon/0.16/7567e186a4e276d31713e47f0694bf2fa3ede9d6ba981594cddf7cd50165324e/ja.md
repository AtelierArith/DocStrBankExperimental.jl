```
backward_induction(ddp, J[, v_term=zeros(num_states(ddp))])
```

$$
J
$$

期間の有限ホライズン離散動的プログラムを、定常報酬$r$、遷移確率関数$q$、割引因子$\beta \in [0, 1]$を用いて逆帰納法で解きます。

最適価値関数$v^{\ast}_1, \ldots, v^{\ast}_{J+1}$およびポリシー関数$\sigma^{\ast}_1, \ldots, \sigma^{\ast}_J$は、$v^{\ast}_{J+1} = v_{J+1}$により得られ、

$$
v^{\ast}_j(s) = \max_{a \in A(s)} r(s, a) +
\beta \sum_{s' \in S} q(s'|s, a) v^{\ast}_{j+1}(s')
\quad (s \in S)
$$

および

$$
\sigma^{\ast}_j(s) \in \operatorname*{arg\,max}_{a \in A(s)}
            r(s, a) + \beta \sum_{s' \in S} q(s'|s, a) v^*_{j+1}(s')
            \quad (s \in S)
$$

が成り立ちます。ここで、$j= J, \ldots, 1$であり、終端価値関数$v_{J+1}$は外生的に`v_term`として与えられます。

# パラメータ

  * `ddp::DiscreteDP{T}` : モデルパラメータを含むオブジェクト
  * `J::Integer`: 決定期間の数
  * `v_term::AbstractVector{<:Real}=zeros(num_states(ddp))`: 状態の数$n$に等しい長さの終端価値関数

# 戻り値

  * `vs::Matrix{S}`: 形状(n, J+1)の配列で、`vs[:,j]`は期間$j = 1, \ldots, J+1$における最適価値関数を含みます。
  * `sigmas::Matrix{Int}`: 形状(n, J)の配列で、`sigmas[:,j]`は期間$j = 1, \ldots, J$における最適ポリシー関数を含みます。
