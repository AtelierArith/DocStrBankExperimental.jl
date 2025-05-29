```
@generate_static_methods numbers 1argfuns 2argfuns
```

このマクロは、関数が `Static` 引数のみで呼び出されたときに `Static` 数値を返すメソッドを作成します。

入力は、すべての関数の入力および出力としてテストされるリテラル数値のリストである必要があります。

オプションで、4番目の引数として、入力としてではなく結果としてのみ考慮される数値のリストを指定できます。

例:

```
@generate_static_methods (0, 1) (sin, cos) (+, -)
```

は、以下のすべてのメソッド定義を作成します:

```
sin(::StaticInteger{0}) = StaticInteger{0}()
cos(::StaticInteger{0}) = StaticInteger{1}()
+(::StaticInteger{0}, ::StaticInteger{0}) = StaticInteger{0}()
+(::StaticInteger{0}, ::StaticInteger{1}) = StaticInteger{1}()
+(::StaticInteger{1}, ::StaticInteger{0}) = StaticInteger{1}()
-(::StaticInteger{0}, ::StaticInteger{0}) = StaticInteger{0}()
-(::StaticInteger{1}, ::StaticInteger{0}) = StaticInteger{0}()
-(::StaticInteger{1}, ::StaticInteger{1}) = StaticInteger{1}()
```

（注: マクロはローカルスコープで実行されます。`Base` の関数は拡張する前にインポートする必要があります。）
