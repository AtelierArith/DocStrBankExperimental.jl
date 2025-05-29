```
TruncatedSource <: IO
```

IOオブジェクトをラップして、読み取るべき量だけを読み取り、それ以上は読み取らないようにします。

この抽象型から継承されたオブジェクトは、`bytesavailable(io)`および`eof(io)`を除くすべての読み取り指向のIOメソッドをラップされたストリームに渡します。継承された型は*必ず*次のメソッドを実装しなければなりません：

  * `TruncatedStreams.unwrap(::TruncatedSource)::IO`: ラップされたIOストリームを返します。
  * `Base.eof(::TruncatedSource)::Bool`: ストリームがこれ以上バイトを生成できないかどうかを報告します。

切り捨てを実装するために、これらのメソッドのいくつかを実装する必要があるでしょう：

  * `Base.unsafe_read(::TruncatedSource, p::Ptr{UInt8}, n::UInt)::Nothing`: ストリームからメモリのポインタ`p`が指す場所に`n`バイトをコピーします。
  * `Base.read(::TruncatedSource, T::Type)::T`: ストリームから型`T`のオブジェクトを読み取り、返します。
  * `Base.bytesavailable(::TruncatedSource)::Int`: EOFまでまたはバッファの再充填が必要になるまで、ストリームから読み取ることができるバイト数を報告します。
  * `Base.seek(::TruncatedSource, p::Integer)`および`Base.seekend(::TruncatedSource)`: ストリームを位置`p`またはストリームの終わりにシークします。
  * `Base.reset(::TruncatedSource)`: マークされたストリームを保存された位置にリセットします。
  * `Base.reseteof(::TruncatedSource)::Nothing`: EOFステータスをリセットします。
  * `Base.peek(::TruncatedSource[, T::Type])::T`: ストリームから型`T`の次のオブジェクトを読み取り、返しますが、次の読み取りのためにストリーム内のバイトはそのままにします。

次のメソッドは、`TruncatedSource`のすべての機能が正常に動作するために、ラップされたIO型によって*必ず*実装されなければなりません：

  * `Base.eof(::IO)::Bool`
  * `Base.read(::IO, ::Type{UInt8})::UInt8`

ラップされたストリームは、切り捨てられたストリームのシークおよびスキップが正しく機能するために、`Base.seek`および`Base.skip`も実装する必要があります。さらに、`Base.position`は、`Base.seek`のいくつかの実装が正しく機能するために実装する必要があります。
