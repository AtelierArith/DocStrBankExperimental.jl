```
 @NLparameters(model, args...)
```

モデル `model` に複数の非線形パラメータを作成して返します。これは [`@NLparameter`](@ref) マクロと同様の方法です。

モデルは最初の引数でなければならず、複数のパラメータは `begin ... end` ブロック内で複数行にわたって追加できます。異なるパラメータは、以下の例のように別々の行に配置する必要があります。

このマクロは、定義されたパラメータを含むタプルを返します。

!!! compat
    このマクロは、レガシー非線形インターフェースの一部です。 [非線形モデリング](@ref) に文書化されている新しい非線形インターフェースの使用を検討してください。ほとんどの場合、次のような呼び出しを置き換えることができます。

    ```julia
    @NLparameters(model, begin
        p == value
    end)
    ```

    を

    ```julia
    @variables(model, begin
        p in Parameter(value)
    end)
    ```


## 例

```jldoctest
julia> model = Model();

julia> @NLparameters(model, begin
           x == 10
           b == 156
       end);

julia> value(x)
10.0
```
