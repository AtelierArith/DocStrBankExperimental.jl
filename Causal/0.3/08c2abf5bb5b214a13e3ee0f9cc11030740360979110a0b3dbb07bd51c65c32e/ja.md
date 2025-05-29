```
evolve!(comp::AbstractSource, u, t)
```

何もしません。`u`は`input`の値で、`t`は時間です。

```
evolve!(comp::AbstractSink, u, t)
```

`t`を時間バッファ`timebuf`に書き込み、`u`を`comp`の`databuf`に書き込みます。`u`は`input`の値で、`t`は時間です。

```
evolve!(comp::AbstractStaticSystem, u, t)
```

`comp`が`AbstractMemory`である場合、`u`を`comp`の`buffer`に書き込みます。それ以外の場合、何も行われません。`u`は`input`の値で、`t`は時間です。

```
evolve!(comp::AbstractDynamicSystem, u, t)
```

初期条件`x`（`x`は`comp`の現在の状態）に対して、時間区間`(comp.t, t)`のシステムの微分方程式を解きます。`u`は`(comp.t, t)`のために定義された入力関数です。`comp`は計算された状態と時間`t`で更新されます。
