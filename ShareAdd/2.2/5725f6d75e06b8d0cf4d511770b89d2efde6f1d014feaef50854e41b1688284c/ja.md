```
パッケージ ShareAdd v2.2.0
```

このJuliaパッケージはマクロ`@usingany`をエクスポートします。このマクロは、パッケージがまだ利用可能でない場合にそれらを利用可能にし、`using`キーワードでロードします。

  * 環境の`LOAD_PATH`にパッケージが利用可能であれば、それで問題ありません。
  * 共有環境にパッケージが利用可能であれば、その環境が`LOAD_PATH`に追加されます。
  * それ以外の場合、パッケージをインストールできる場合は、各パッケージをインストールする環境を選択するように促されます。
  * パッケージがどのレジストリにもリストされていない場合、エラーが発生します。

ShareAddには、共有環境を管理するのに役立つユーティリティ関数もあります。例えば：

  * [`ShareAdd.info`](@ref): 共有環境および/またはパッケージに関する情報をリストします。
  * [`ShareAdd.update`](@ref): パッケージまたは環境を更新します。
  * [`ShareAdd.delete`](@ref): パッケージまたは環境を削除します。
  * [`@showenv`](@ref): デスクトップGUIで環境フォルダを開きます。

これらの関数は公開されていますが、名前の衝突を避けるためにエクスポートされていません。`@showenv`マクロはエクスポートされています。

# 例

```julia-repl
julia> ShareAdd.update("Plots")
  プロジェクトを`~/.julia/environments/Plotting`でアクティブ化しています
# ... 更新情報の画面が表示されます
julia> @usingany Plots
julia> plot(xs, ys)
```

参考：ドキュメント文字列を参照してください。

ドキュメント：https://eben60.github.io/ShareAdd.jl/

パッケージのローカルパス：/home/terasaki/.julia/packages/ShareAdd/UJfFT/src/ShareAdd.jl
