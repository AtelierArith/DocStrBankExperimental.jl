```
makeswarm(;<keyword arguments>)
```

biowulfで使用されるswarmおよびfitファイルの作成

# 引数

  * `'nthreads=1`：プロセッサあたりのJuliaスレッド数、デフォルト = 1
  * `swarmfile::String="fit"`：swarmによって実行されるswarmfileの名前
  * `juliafile::String="fitscript"`：swarmfile内でjuliaによって呼び出されるファイルの名前
  * `src=""`：StochasticGene.jl/srcを含むフォルダへのパス（StochasticGeneがインストールされていない場合のみ必要）

および関数fitのすべてのキーワード引数(; <keyword arguments> )

fitを参照

注意：キーワード'method'は、fit関数内とは少し異なる方法で処理されます。fitでは、関数（すなわち、DifferentialEquations.jlで使用される数値法関数）または数値法と階層モデル用のBoolのタプルです。しかし、biowulf.jlでは、数値法はStringでなければなりません。つまり、Tsit5()のために"Tsit5()"を使用します。これは、Juliaが関数を書き込むときに、単に書き込むのではなく、数値法を解析するためです。
