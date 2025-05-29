```
connect(systems, connections; external_inputs, external_outputs = (:), verbose = true, unique = true, kwargs...)
```

名前付きの入力と出力を使用してブロック接続を作成します。

加算および減算ノードは、`D` 行列のみを持つシステム、すなわち線形結合ノードを作成することによって実現されます。

# 引数:

  * `systems`: 接続される名前付きシステムのベクター
  * `connections`: 出力 => 入力のペアのベクターで、各ペアは出力を入力にマッピングします。各出力は `systems` のいずれかの出力として現れなければならず、同様に各入力は `systems` のいずれかの入力として現れなければなりません。すべての入力はユニークな名前を持つ必要があり、すべての出力も同様ですが、入力は出力と同じ名前を持つことができます。以下の例では、接続 `:uP => :uP` は `addP` ブロックの出力 `:uP` を `P` の入力 `:uP` に接続します。
  * `external_inputs`: 構築されたシステムで入力として使用される外部信号。すべての信号を示すには `(:)` を使用します。
  * `external_outputs`: 構築されたシステムの出力。すべての信号を示すには `(:)` を使用します。
  * `verbose`: 接続がない信号に対して警告を発行します。
  * `unique`: `true` の場合、すべての入力名はユニークでなければなりません。`false` の場合、単一の外部入力信号は同じ名前の複数の入力ポートに接続されることができます。

注意: 正のフィードバックが使用されており、負のフィードバックで接続されることを意図したコントローラーは否定されなければなりません。

例: 次の複雑なフィードバック相互接続

```
                 yF
               ┌────────────────────────────────┐
               │                                │
    ┌───────┐  │  ┌───────┐        ┌───────┐    │    ┌───────┐
uF  │       │  │  │       | yR     │       │ yC │ uP │       │   yP
────►   F   ├──┴──►   R   │────+───►   C   ├────+────►   P   ├───┬────►
    │       │     │       │    │   │       │         │       │   │
    └───────┘     └───────┘    │   └───────┘         └───────┘   │
                               │                                 │
                               └─────────────────────────────────┘
```

は次のように作成できます。

```
F = named_ss(ssrand(1, 1, 2, proper=true), x=:xF, u=:uF, y=:yF)
R = named_ss(ssrand(1, 1, 2, proper=true), x=:xR, u=:uR, y=:yR)
C = named_ss(ssrand(1, 1, 2, proper=true), x=:xC, u=:uC, y=:yC)
P = named_ss(ssrand(1, 1, 3, proper=true), x=:xP, u=:uP, y=:yP)

addP = sumblock("uP = yF + yC") # P の前の和ノード
addC = sumblock("uC = yR - yP") # C の前の和ノード

connections = [
    :yP => :yP # 出力から入力へ
    :uP => :uP
    :yC => :yC
    :yF => :yF
    :yF => :uR
    :uC => :uC
    :yR => :yR
]
external_inputs = [:uF] # 外部入力

G = connect([F, R, C, P, addP, addC], connections; external_inputs)
```

外部入力を複数のポイントに接続する場合は、`splitter` を使用して信号をユニークな名前のセットに分割し、それを接続に使用します。
