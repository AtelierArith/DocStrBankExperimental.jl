`A,B = ortho_latin(n)` は、直交する `n`×`n` ラテン方格のペアを返します。

`A,B = ortho_latin(n,true)` は、お互いの転置である直交ラテン方格のペアを返します。

`A,B = ortho_latin(n,r,s)` は、ラテン方格 `latin(n,r)` と `latin(n,s)` を構築し、それらが直交している場合は答えとして返します。（そうでない場合はエラーをスローします。）参照: `find_ortho_parameters`。
