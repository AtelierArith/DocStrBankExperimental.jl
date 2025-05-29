```
read_tree(
	nwk_filename::AbstractString;
	node_data_type=DEFAULT_NODE_DATATYPE,
    label,
    force_new_labels=false,
    check=true,
)
read_tree(io::IO; kwargs...)
```

Newickファイルを読み込み、そこから`Tree{node_data_type}`オブジェクトを作成します。入力ファイルに異なる行に複数のNewick文字列が含まれている場合、出力は`Tree`オブジェクトの配列になります。

呼び出し`node_data_type()`は、`TreeNodeData`のサブタイプの有効なインスタンスを返さなければなりません。独自のサブタイプを実装することもできますし、すでに実装されているものについては`?TreeNodeData`を参照してください。デフォルトは`EmptyData`です。

`force_new_labels=true`を使用すると、すべての内部ノードの名前を強制的に変更できます。デフォルトでは、ツリーには`default_tree_label()`を呼び出すことでラベルが割り当てられます。これは`label`引数を使用して変更できます。

Newick文字列を含む変数があり、それからツリーを構築したい場合は、代わりに`parse_newick_string`を使用してください。

## ラベルに関する注意

`Tree`型はノードをラベルで識別します。これは、ラベルが一意である必要があることを意味します。このため、ツリーを読み込む際には以下のことが行われます：

  * 内部ノードにラベルがない場合、`"NODE_i"`の形式で一意のラベルが作成されます。
  * ノードにツリー内で以前に見つかったラベルがある場合、一意にするためにランダムな識別子がそれに追加されます。識別子は`randstring(8)`を使用して作成されるため、一意性は技術的には保証されません。
  * `force_new_labels`が使用される場合、ノードラベルに一意の識別子が追加されます。
  * Newickファイル内のノードラベルが信頼度/ブートストラップ値として識別される場合、それらにランダムな識別子が追加されます。ツリー内で一意であってもです。どのラベルが信頼度値として識別されるかは、`?TreeTools.isbootstrap`を参照してください。
