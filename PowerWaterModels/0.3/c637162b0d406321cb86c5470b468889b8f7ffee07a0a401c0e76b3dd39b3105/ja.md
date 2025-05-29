最大の時間隣接の発電変数間の差を最小化する目的。なお、この関数は目的を適切にモデル化するためにいくつかの補助変数と制約を導入します。数学的には、目的と補助項は次のようにモデル化されます：

$$
    \begin{aligned}
    & \text{minimize} & & z \\
    & \text{subject to} & & z \geq pg_{i, c, t} - pg_{i, c, t-1}, \, \forall i \in \mathcal{G}, \, \forall c \in \mathcal{C}, \, \forall t \in \{2, 3, \dots, T\} \\
    & & & z \geq pg_{i, c, t-1} - pg_{i, c, t}, \, \forall i \in \mathcal{G}, \, \forall c \in \mathcal{C}, \, \forall t \in \{2, 3, \dots, T\} \\
    & & & z \geq 0 \\
    & & & x \in \mathcal{X},
    \end{aligned}
$$

ここで、$\mathcal{G}$は発電機の集合、$\mathcal{C}$は導体の集合、$\{2, 3, \dots, T\}$は非開始時間インデックスです。さらに、$x \in \mathcal{X}$は問題の定式化の残りを表し、すなわちこの説明に関連しない変数と制約です。
