```
function SegmentIntegrator(
	EG::ElementGeometry,
	[kernel!::Function],
	oa_args::Array{<:Tuple{<:Any, DataType},1};
	kwargs...)
```

指定されたジオメトリEGのセグメント上で積分できるSegmentIntegratorを生成します。これを行うために、各ガウス点で指定された演算子評価を評価し、（提供されている場合は）カーネル関数で後処理し、ガウス重みで結果を累積します。カーネルが指定されていない場合、引数は直接積分されます。カーネルが提供されている場合は、インターフェースに準拠する必要があります。

```
kernel!(result, eval_args, qpinfo)
```

ここで、qpinfoは現在のガウス点での情報にアクセスすることを可能にします。さらに、結果の長さはkwargsを介して指定する必要があります。

評価は、initialize!の後にintegrate_segment!関数を介してトリガーできます。

演算子評価は、タグ（未知数またはベクトル内の位置を識別するため）とFunctionOperatorをペアにしたタプルです。

キーワード引数：

  * factor: アセンブリ中に掛け算されるべき因子。デフォルト: 1
  * resultdim: 結果フィールドの次元（デフォルト = 引数の長さ）。デフォルト: 0
  * matrix_mode: 統合器はFEspaceの基底関数を個別に統合して、解をセグメント積分にマッピングする行列を組み立てます（カーネルが線形である必要があります）。デフォルト: false
  * name: 出力に使用される演算子の名前。デフォルト: ''SegmentIntegrator''
  * params: カーネル関数のqpinfo引数で利用可能にするべきパラメータの配列。デフォルト: nothing
  * quadorder: ガウス順序。デフォルト: ''auto''
  * bonus_quadorder: quadorderに追加される追加のガウス順序。デフォルト: 0
  * entry*tolerance: スパース行列にエントリを追加するための閾値（matrix*modeのみ）。デフォルト: 0
  * verbosity: 冗長性レベル。デフォルト: 0
