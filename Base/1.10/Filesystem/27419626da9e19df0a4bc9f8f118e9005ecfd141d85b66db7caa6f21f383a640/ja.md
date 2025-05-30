```
cp(src::AbstractString, dst::AbstractString; force::Bool=false, follow_symlinks::Bool=false)
```

`src`から`dst`にファイル、リンク、またはディレクトリをコピーします。`force=true`の場合、既存の`dst`は最初に削除されます。

`follow_symlinks=false`で、`src`がシンボリックリンクの場合、`dst`はシンボリックリンクとして作成されます。`follow_symlinks=true`で、`src`がシンボリックリンクの場合、`dst`は`src`が指すファイルまたはディレクトリのコピーになります。`dst`を返します。

!!! note
    `cp`関数は`cp`コマンドとは異なります。`cp`関数は常に`dst`がファイルであると仮定して動作しますが、コマンドは`dst`がディレクトリかファイルかによって異なる動作をします。`dst`がディレクトリのときに`force=true`を使用すると、`dst`ディレクトリ内のすべての内容が失われ、`dst`は`src`の内容を持つファイルになります。

