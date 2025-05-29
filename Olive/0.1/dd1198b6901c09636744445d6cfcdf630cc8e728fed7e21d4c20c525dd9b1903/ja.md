```julia
build(c::Connection, cm::ComponentModifier, p::Project{<:Any}) -> ::Component{:div}
```

Oliveプロジェクトのためのキャッチオール/デフォルトの`build`関数。この関数を拡張して、新しい`Project`タイプの構築方法を変更します。デフォルトでは、生成されたセルを子として持つシンプルなウィンドウを作成します。セルは、`build`を呼び出すことで同様に生成されます。

```julia
using Olive; Olive.start()

# (環境をインスタンス化するためにオリーブリンクをクリックしてください)
import Olive: build

build(c::Connection, cm::ComponentModifier, p::Project{:newproject}) = begin
    div(p.id, children = [build(c, cm, p, cell) for cell in p[:cells]])
end

# プロジェクトタイプをファイルや拡張から読み込まない場合は、読み込む必要があります:
push!(Olive.CORE.open[1].projects, Project{:newproject}(""))

# ページをリフレッシュしてください!
```

`Project`に関して見るべき**重要な**関数は以下の通りです:

  * `source_module!`
  * `check!`
  * `work_preview`
  * `open_project`
  * `close_project`
  * `save_project`
  * `save_project_as`
  * `olive_save`
  * `build_tab`
  * `style_tab_closed!`
  * `tab_controls`
  * `switch_pane!`
  * `step_evaluate`

特に、すべての`Cell`関数はプロジェクトにもディスパッチされるため、異なるプロジェクトが異なるセルタイプで何をするかを変更するためにこれらのメソッドを使用することもできます。
