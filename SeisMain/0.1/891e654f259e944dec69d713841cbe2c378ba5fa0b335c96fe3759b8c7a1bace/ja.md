```
  SeisPatchProcess(in,out;<keyword arguments>)
```

ディスクからデータを読み込み、多次元の重なり合うパッチに分割し、プロセスを適用し、テーパーでパッチをマージし、ディスクに書き込みます。

パッチの処理は、コードを実行することで並行して行うことができます（例えば）： julia -p 2 script_name.jl

重要なお知らせ：すべてのプロセッサでグローバル変数 f と f*param を宣言する必要があります。これは、メイン関数で次のように入力することで行えます： @everywhere global f*param = ["style"=>"mxmyhxhy", "Niter"=> 100, "alpha"=>1,"fmax"=>80] @everywhere global f = [SeisPOCS]

f は次の構文を持つ関数の配列です： d2, h2 = f(d1,h1,f_param)、ここで param は関数のパラメータの辞書 (Dict) です。

param にはパッチ処理およびアンパッチ処理のためのパラメータが含まれている必要があります。

コードを実行するには、次のように入力します： julia -p 4 my_code.jl ここで 4 は使用したいプロセッサの数に置き換えることができます。 *クレジット: A. Stanton*
