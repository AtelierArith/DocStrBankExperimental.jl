```
@msg [Msg] A B C
```

空の構造体をメッセージタイプとして定義します。`Msg`は既存の抽象データ型です。

`@msg Msg A B C`を呼び出すことは、次のことと同等です。

```
struct A <: Msg end
struct B <: Msg end
struct C <: Msg end
```

`@msg D E F`を呼び出すことは、次のことと同等です。

```
struct D end
struct E end
struct F end
```
