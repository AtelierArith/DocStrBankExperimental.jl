```
@required MyInterface func(::Foo, ::MyInterface)
@required MyInterface function func(::Foo, ::MyInterface) end
@required MyInterface begin
    foo(::B, ::MyInterface)
    bar(::A, ::MyInterface)
end
```

与えられた関数シグネチャ内の `MyInterface` のすべての出現をインターフェース `MyInterface` の一部としてマークします。また、必須の関数を実装していない引数で呼び出されたときに [`NotImplementedError`](@ref) をスローするフォールバックメソッドを定義します。

`MyInterface` が抽象型でない場合や、与えられた式が示された3つのスタイルに準拠していない場合は `ArgumentError` をスローします。2番目のスタイルの関数本体は空であることが期待されます - `@required` はフォールバック実装をユーザーが実装可能なインターフェースの一部としてマークするために使用できません。その唯一の目的は、ユーザーがそのインターフェースを期待する関数が機能するために実装する必要があるAPIの部分をマークすることです。
