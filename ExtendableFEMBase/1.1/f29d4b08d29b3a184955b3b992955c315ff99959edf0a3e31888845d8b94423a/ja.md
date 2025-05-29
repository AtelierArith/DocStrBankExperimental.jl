```
function Pointevaluator(
	[kernel!::Function],
	oa_args::Array{<:Tuple{<:Any, DataType},1};
	kwargs...)
```

指定された演算子評価を任意の点で評価できる PointEvaluator を生成します。カーネル関数が指定されていない場合、引数は直接与えられます。カーネルが提供されている場合、引数はそれに応じて後処理され、カーネルはインターフェースに準拠する必要があります。

```
kernel!(result, eval_args, qpinfo)
```

ここで、qpinfo は現在の評価点での情報にアクセスすることを可能にします。さらに、結果の長さは kwargs を介して指定する必要があります。

評価は、initialize! 呼び出しの後に evaluate 関数を介してトリガーできます。

演算子評価は、タグ（未知数またはベクトル内の位置を識別するため）と FunctionOperator をペアにしたタプルです。

キーワード引数:

  * resultdim: 結果フィールドの次元（デフォルト = 演算子の長さ）。デフォルト: 0
  * params: カーネル関数の qpinfo 引数で利用可能にする必要があるパラメータの配列。デフォルト: 何もなし
  * name: 出力で使用される演算子の名前。デフォルト: ''PointEvaluator''
  * verbosity: 詳細レベル。デフォルト: 0

```
