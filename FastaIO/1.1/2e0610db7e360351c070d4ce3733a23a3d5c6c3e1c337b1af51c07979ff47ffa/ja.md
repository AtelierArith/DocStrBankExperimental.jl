このモジュールは、Juliaで[FASTA形式](http://en.wikipedia.org/wiki/FASTA_format)のファイルを解析および書き込む方法を提供します。軽量で高速になるように設計されており、解析メソッドは[kseq.h](http://lh3lh3.users.sourceforge.net/kseq.shtml)に触発されています。ファイルをオンザフライで読み書きでき、メモリには一度に1つのエントリのみを保持し、gzip圧縮されたファイルの読み書きも可能です。

[`FastaReader`](@ref)、[`FastaWriter`](@ref)、[`readfasta`](@ref)、[`writefasta`](@ref)、[`readentry`](@ref)および[`writeentry`](@ref)を参照してください。
