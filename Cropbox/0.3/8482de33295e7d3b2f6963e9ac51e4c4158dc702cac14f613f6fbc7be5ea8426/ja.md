```
dive(s)
```

システム `s` のインスタンスを、ツリー構造で表示される変数の階層をナビゲートすることで検査します。

上矢印/下矢印キーを押すことでナビゲーションが可能です。'enter' を押すとより深いレベルにダイブし、'q' を押すと戻ります。ツリーの葉ノードは変数に関する `look` の出力を表示します。再度 'enter' を押すと変数自体が返され、REPL に戻ります。

ターミナル環境でのみ動作し、Jupyter Notebook では動作しません。

関連情報: [`look`](@ref)

# 引数

  * `s::System`: 対象システムのインスタンス。

# 例

```julia-repl
julia> @system S(Controller) begin
           a => 1 ~ preserve(parameter)
       end;

julia> s = instance(S);

julia> dive(s)
S
 → context = <Context>
   config = <Config>
   a = 1.0
```
