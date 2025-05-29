```
installkernel(name::AbstractString, options::AbstractString...;
              julia::Cmd,
              specname::AbstractString,
              displayname::AbstractString,
              env=Dict())
```

新しいJuliaカーネルをインストールします。ここで、指定された`options`は`julia`実行可能ファイルに渡され、ユーザーが目にするカーネル名は`name`に続いてJuliaのバージョンが付加され、`env`辞書が環境に追加されます。

新しいカーネル名は`installkernel`によって返されます。例えば：

```julia
kernelpath = installkernel("Julia O3", "-O3", env=Dict("FOO"=>"yes"))
```

は、`julia`が`-O3`最適化フラグで起動され、`FOO=yes`が環境変数に含まれる新しいJuliaカーネルを作成します。

`displayname`引数は、Jupyterカーネルリストに表示される名前をカスタマイズするために使用できます。

返される`kernelpath`は、インストールされたカーネルディレクトリのパスで、例えば`/...somepath.../kernels/julia-o3-1.6`（Julia 1.6の場合）のようになります。`specname`引数を渡すことで、このディレクトリの名前を変更できます（デフォルトでは`name`のスペースがハイフンに置き換えられ、`-`ハイフン、`.`ピリオド、`_`アンダースコア以外の特殊文字は`_`アンダースコアに置き換えられます）。

カーネルは`rm(kernelpath, recursive=true)`を呼び出すことでアンインストールできます。

キーワード引数`julia`を介してJuliaを実行するカスタムコマンドを指定できます。例えば、Dockerコンテナ内でJuliaカーネルが実行されていることを指定したい場合（ただしJupyterはその外部で実行されます）、次のようにそのようなコンテナインスタンス内から`installkernel`を呼び出すことができます（または類似の方法で）：

```julia
installkernel(
    "Julia via Docker",
    julia = `docker run --rm --net=host
        --volume=/home/USERNAME/.local/share/jupyter:/home/USERNAME/.local/share/jupyter
        some-container /opt/julia-1.x/bin/julia`
)
```
