"コンポジット"構造体を作成するために、1つの構造体のフィールドを別の構造体にスプライスします。例えば：

```julia
struct Foo{X,Y}
    x :: X
    y :: Y
end

@composite struct Bar{X,Y,Z}
    Foo{X,Y}...
    z :: Z
end

# 定義するのと同等：
struct Bar{X,Y,Z}
    x :: X
    y :: Y
    z :: Z
end
```

スプライスされた型に型パラメータがある場合、それらはすべて明示的に指定する必要があります（上記の`X`と`Y`のように）。複数の型は、フィールド名が重複しない限り、任意の順序でスプライスできます。

`Base.@kwdef`と互換性があり、`@composite @kwdef struct ... end`を使用します。スプライスされた型自体がキーワードコンストラクタを持っている必要があり、そのデフォルトはコンポジット型に伝播します：

```julia
@kwdef struct Foo
    x = 1
    y
end

@composite @kwdef struct Bar
    Foo...
    z = 3
end

Bar(y=2) # Bar(1,2,3)を返します
```

このマクロは標準の構造体を生成するため、コンポジット構造体の使用に制限はありません（コンポジティングは再帰的に行うこともできます）。

このように構造体を拡張することは継承を模倣でき、元の構造体と拡張された構造体の両方に共通の抽象スーパタイプを与えることで強力になります（ユーザーは必要に応じて通常のJulia構文を使用して指定できます）。

## 注意

このパッケージは、[Mixers.jl](https://github.com/rafaqz/Mixers.jl)や[Classes.jl](https://github.com/rjplevin/Classes.jl)にかなり似ていますが、特別なマクロで装飾された構造体だけでなく、任意の構造体を「拡張」できる点が異なります（これらのパッケージのケースでは）。また、`Base.@kwdef`との互換性がある点でもユニークです。Classes.jlのOOP抽象型階層の自動作成はなく、代わりにユーザーが明示的に指定することになります。[この](https://discourse.julialang.org/t/eval-scoping-in-macros-or-removing-eval-completely/54602/3?u=marius311)ディスカッションコメントに触発されています。
