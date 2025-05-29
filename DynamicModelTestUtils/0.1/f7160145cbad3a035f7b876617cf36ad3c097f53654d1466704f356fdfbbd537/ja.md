```
compare(
    new_sol::SciMLBase.AbstractTimeseriesSolution,
    reference::DataFrame,
    cmp=DefaultComparison(); to_name=string, warn_observed=true)
```

`compare`は、`new_sol`の結果を`reference`の結果と比較します。`reference`は実験または以前のモデル実行からのものである可能性があります。`reference`の形式は、[`discretize_solution`](@ref)によって生成されるものです：

  * 測定が行われた時間を示す「timestamp」という名前の列（提供されたソリューションと同じ時間基準に基づいています）
  * 完成したシステム`new_sol`の名前と一致する名前の列（完全修飾）

`new_sol`が密である場合、離散化ノードは`reference`と一致する必要はなく、代わりに補間関数が使用されます。密でない場合、ユーザーは保存された状態が`reference`データの「timestamp」と同じ時間にあることを確認する必要があります。

`compare`は、`cmp`で指定された比較方法を使用して2つのソリューションを比較します。デフォルトでは、[`DefaultComparison`](@ref)を使用します（これは観測値ごとにl1、l2、およびrms比較を提供します）が、自分自身のものを渡すこともできます。詳細については`DefaultComparison`を参照してください。

2つのオプションの名前付きパラメータは、`to_name`（これは`new_sol`の記号変数をデータフレームの有効な列名に変換するために使用されます）と、`warn_observed`（これは`compare`が観測値と非観測値を比較することについて不満を言うかどうかを制御します）です。回帰テストのために`warn_observed`をオンにしておくことをお勧めします（MTKがシステムの簡略化を変更したときに通知が表示されます）。
