`ParamDict`は、辞書とマップを組み合わせたもので、辞書のサポートの画像であるいくつかのドメインのパラメータ化です。

もし`Ω`がドメインであり、関数`κ : P → Ω`によってパラメータ化されている場合、`ParamDict`は`P`上で定義された辞書であり、各点`t ∈ P`は`x = κ(t) ∈ Ω`として識別されます。`ParamDict`は`P`上の他の辞書と同様に機能します。

`Ω`上で定義された`MappedDict`との違いに注意してください。マップされた辞書に対する操作は、簡単に逆転可能なマップを必要とします。
