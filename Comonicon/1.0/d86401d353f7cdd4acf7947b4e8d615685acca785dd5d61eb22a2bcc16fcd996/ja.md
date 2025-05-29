```
@main
@main <関数定義>
```

CLIアプリケーションのメインエントリ。

# クイック例

```julia
# スクリプトまたはモジュール内で

"""
2つの数を合計します。

# 引数

- `x`: 最初の数
- `y`: 2番目の数

# オプション

- `-p, --precision=<type>`: 計算の精度。

# フラグ

- `-f, --fastmath`: fastmathを有効にします。

"""
@main function sum(x, y; precision::String="float32", fastmath::Bool=false)
    # 実装
    return
end
```

# CLI定義とJulia構文マッピング

**位置引数** 通常の入力で、これらはJulia関数引数としてマッピングされます。例：

```shell
sum 1 2
```

`sum`はコマンドで、`1`、`2`は位置引数です。

**オプション** 構文 `--<name>=<value>` または `--<name> <value>` の引数で、これらはJuliaキーワード引数としてマッピングされます。例：

```shell
sum --precision=float32 1 2
```

`--precision`はコマンド`sum`のオプションで、値は`float32`です。

**短いオプション** 構文 `-<letter>=<value>` または `-<letter><value>` または `--<letter> <value>` の引数で、文字は通常、通常のオプションの最初の文字です。例：

```shell
sum -pfloat32 1 2
```

`-p`は`--precision`と同じですが、短縮形です。これは対応するドキュメンテーション文字列を書くことで有効になります（次のセクションのドキュメンテーション文字列構文を参照）。

**フラグ** オプションのように、値なしで、例 `--<name>`、これは`Bool`型の特別なキーワード引数にマッピングされ、デフォルト値は`false`です。例：

```shell
sum --fastmath
```

**短いフラグ** 構文 `-<letter>` のフラグで、文字は対応する通常のフラグの最初の文字である必要があります。例：

```shell
sum -f
```

# ドキュメント文字列構文

異なる種類の入力は、それぞれ異なるレベル1セクション（マークダウン構文 `#<セクション名>`）を持たなければなりません。

ドキュメント文字列にはセクション名が必要です：

  * `#Args` または `#Arguments` 位置引数のドキュメントを宣言するため。
  * `#Options` オプションのドキュメントを宣言するため。
  * `#Flags` フラグのドキュメントを宣言するため。

# 例

最も簡単な使用法は、次のコマンドを作成することです。

```julia
"""
例のコマンド

# 引数

- `x`: 最初の引数
- `y`: 2番目の引数
- `z`: 最後の引数

# フラグ

- `-f, --flag`: フラグ、オプションで短いフラグにすることができます。

# オプション

- `-o, --option=<int>`: オプション、オプションで短いオプションにすることができます。

"""
@cast function mycommand(x, y, z; flag::Bool=false, option::Int=2)
    # いくつかの実装
    return
end

@cast function myothercommand(xs...)
    # 可変引数を持つ別のコマンド
    return
end

"""
私のメインコマンド。
"""
@main # エントリを宣言
```

これはコマンドラインで `mycommand 1 2 3 --flag` として使用できます。また、詳細なヘルプ情報を確認するには、単に `-h` と入力することもできます。

コマンドラインのドキュメントは、あなたのJuliaドキュメント文字列から自動的に生成されます。

もしコマンドの階層が深い場合は、Juliaモジュールに`@cast`を置くこともできます。

```julia
using Comonicon
@cast module NodeCommand

using Comonicon

@cast module NodeSubCommand
using Comonicon
@cast bar(x) = println("bar $x")
end
@cast foo(x) = println("foo $x")
@main
end

NodeCommand.command_main()
```
