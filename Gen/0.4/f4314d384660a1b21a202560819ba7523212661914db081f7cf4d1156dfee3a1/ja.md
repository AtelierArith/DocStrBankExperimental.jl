```
選択
```

アドレスの選択のための抽象型。

すべての選択は以下のメソッドを実装します：

```
Base.in(addr, selection)
```

アドレスは選択されていますか？

```
Base.getindex(selection, addr)
```

指定されたアドレスでのサブ選択を取得します。

```
Base.isempty(selection)
```

選択が空であることが保証されていますか？

```
get_address_schema(T)
```

浅いコンパイル時アドレススキーマを返します。ここで `T` は選択の具体的な型です。
