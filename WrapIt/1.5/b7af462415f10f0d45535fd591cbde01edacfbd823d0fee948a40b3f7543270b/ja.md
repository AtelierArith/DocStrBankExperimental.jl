wrapit(;`args`)

[wrapit](https://www.github.com/grasph/wrapit) コマンドを起動します。コマンドオプションは、次の形式の関数引数として渡されます。

  * 引数を取るオプションの場合は <option name>=<option value>。例：`resource_dir=/usr/lib/...` は `--resource-dir=/usr/lib...` オプションを渡します。
  * 引数のないオプションの場合は <option name>=true。例：`force=true` は `--force` オプションを渡します。

引数名には、オプション名で使用されるダッシュの代わりにアンダースコアが使用されます。

`wrapit(help=true)` を呼び出すと、オプションのリストが得られます。

`returncode = true` が引数として渡されると、関数は `wrapit` コマンドの終了コードを返します（成功の場合は0）、それ以外の場合は `nothing` を返します。
