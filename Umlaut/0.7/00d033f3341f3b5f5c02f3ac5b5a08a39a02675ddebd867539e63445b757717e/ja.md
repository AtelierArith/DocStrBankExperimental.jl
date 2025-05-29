```
bound(tape::Tape, v::Variable)
V(tape::Tape, v::Integer)
%(tape::Tape, i::Integer)
```

テープ上の操作にバウンドされた変数のバージョンを作成します。短い構文 `tape %i` はREPLで作業する際に便利ですが、コードの読者を驚かせるかもしれません。賢く使いましょう。

# 例:

```
V(3)                # バウンドされていない変数
V(tape, 3)          # バウンドされた変数
bound(tape, 3)      # バウンドされた変数
bound(tape, V(3))   # バウンドされた変数
tape %3             # バウンドされた変数
```
