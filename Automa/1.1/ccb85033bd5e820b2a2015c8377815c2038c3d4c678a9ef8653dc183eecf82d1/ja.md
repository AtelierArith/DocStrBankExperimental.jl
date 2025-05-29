```
CodeGenContext(;
    vars=Variables(:p, :p_end, :is_eof, :cs, :data, :mem, :byte, :buffer),
    generator=:table,
    getbyte=Base.getindex,
    clean=false
)
```

`CodeGenContext` (ctx) を作成します。これは、Automa コード生成のオプションを格納する構造体です。Ctx は、Automa のさまざまなコード生成関数で使用されます。現在、次のオプションを受け取ります（将来のバージョンで追加される可能性があります）。

  * `vars::Variables`: 生成されたコードで使用される変数名。`Variables` 構造体を参照してください。
  * `generator::Symbol`: コード生成メカニズム（`:table` または `:goto`）。テーブル生成器は、状態遷移を決定する整数のベクターを使用して、より小さく、シンプルなコードを生成します。goto生成器は、`@goto` ステートメントの迷路を使用し、より大きく、より複雑なコードを生成しますが、速度は速くなります。
  * `getbyte::Function`（テーブル生成器のみ）: データからバイトにアクセスするための関数 `f(data, p)`。デフォルト: `Base.getindex`。
  * `clean`: 生成されたコードからいくつかの `QuoteNode`（行情報）を削除するかどうか。

# 例

```julia
julia> ctx = CodeGenContext(generator=:goto, vars=Variables(buffer=:tbuffer));

julia> generate_code(ctx, compile(re"a+")) isa Expr
true
```
