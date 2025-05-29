```
@test_reference ファイル名 expr [by] [kw...]
```

式 `expr` を参照 `ファイル名` でテストし、等価性テスト戦略 `by` を使用します。

`test_reference` のパイプラインは次のとおりです：

1. `expr` を前処理する
2. FileIO.jl を介して `ファイル名` を読み込み、前処理する
3. 結果を `by` を使用して比較する
4. インタラクティブセッション（例：`include(test/runtests.jl)`）でテストが失敗した場合、インタラクティブダイアログがトリガーされます。

引数：

  * `ファイル名::String`：マクロ呼び出しを含むファイルへの*相対*パス。
  * `expr`：比較に使用される実際の内容。
  * `by`：等価性テスト関数。明示的に述べられていない場合、デフォルトは `isequal` です。
  * `format`：特定のフォーマットを使用してファイルを強制的に読み込む

# タイプ

`ファイル名` のファイル拡張子と `expr` の評価結果の型により、内容がどのように処理され、比較されるかが決まります。内容は次のように扱われます：

  * `expr` が画像型（例：`AbstractArray{<:Colorant}`）の場合、画像として扱われます。
  * `ファイル名` が `*.sha256` で終わる場合、SHA256 として扱われます。
  * FileIO.jl が処理し、適切なバックエンドが読み込まれている任意のファイルタイプ。
  * フォールバックとしてテキスト。

## FileIO.jl が処理する任意のファイルタイプ

[FileIO.jl](https://github.com/JuliaIO/FileIO.jl) によって読み取ることができる任意のファイルタイプを使用できます。ほとんどの Julia 値は、例えば [BSON.jl](https://github.com/JuliaIO/BSON.jl) や [JLD](https://github.com/JuliaIO/JLD.jl) のようなパッケージを使用して保存できるため、参照テストに使用できます。

## 画像

画像は、エンコーディングおよびデコーディングエラーのほとんどを無視するために異なる `by` を使用して*おおよそ*比較されます。デフォルトの関数は [`psnr_equality`](@ref) から生成されます。

ファイルは、`FileIO` によって処理される一般的な画像ファイル（例：`*.png`）または `ImageInTerminal` によって処理されるテキストコーディングされた `*.txt` ファイルのいずれかです。テキストコーディングされた画像は、ストレージ要件が少なく、`cat` を使用してシンプルなターミナルで参照ファイルを表示することもできます。

## SHA256

`expr` のハッシュと `ファイル名` の内容が比較されます。

!!! tip
    これは、選択したテストケースの戻り値が変更されないことを確認するための便利な低ストレージ方法として役立ちます。


## フォールバック

前処理なしで `expr` と `ファイル名` の内容の等価性を単純にテストします。`ファイル名` を読み込むと `String` が返されることに注意してください。

# 例

```julia
# テキストファイルを値の文字列表現と比較
@test_reference "stringtest1.txt" collect(1:20)

# 絶対許容誤差 10 で数値をテスト
@test_reference "references/string3.txt" 1338 by=(ref, x)->isapprox(ref, x; atol=10)

# 浮動小数点配列 ar を BSON ファイルに保存し、再度比較します。
# Dict が必要であり、カスタム比較関数が必要です。
using BSON
comp(d1, d2) = keys(d1)==keys(d2) &&
    all([ v1≈v2 for (v1,v2) in zip(values(d1), values(d2))])
@test_reference "reftest-files/X.bson" Dict(:ar=>[1, pi, 4.5]) by=comp

# エンコーディングサイズ (5,10) で ImageInTerminal を使用して文字列として保存
using TestImages
@test_reference "camera.txt" testimage("cameraman") size=(5,10)

# 相対パスでフォルダを使用することが許可されています
@test_reference "references/camera.png" testimage("cameraman")

# 画像はハッシュとしても保存できます。ただし、これは
# 等価性のみをチェックできることに注意してください（許容誤差は不可能）
@test_reference "references/camera.sha256" testimage("cameraman")

# カスタムピーク信号対雑音比 (psnr) 閾値で画像をテスト
@test_reference "references/camera.png" testimage("cameraman") by=psnr_equality(20)
```
