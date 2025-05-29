@handlemissings_any(fun, ...)

[`handlemissings`](@ref)を、すでにmissingを受け入れるeltypeに合わせたデフォルトで呼び出します：

  * [`@handlemissings_stub`](@ref)と同様にメソッドをディスパッチします
  * 新しい関数のデフォルトの引数タイプは`Any`になります。デフォルトメソッド（`MissingStragety`引数なし）は作成されません。
  * PassMissingメソッドは、引数のタイプをmissingを含むものに変換せずに元のメソッドを直接呼び出します（[`mgen.passmissing_nonconvert`](@ref)）。
  * HandleMissingメソッドは、`skipmissing()`イテレータオブジェクトを使って元のメソッドを直接呼び出します（[`mgen.handlemissing_skip`](@ref)）。

引数：[`handlemissings`](@ref)を参照してください    

元のメソッドが`eltype`に`missing`を許可する場合、`PassMissing()`を引数として明示的に渡す必要があります。潜在的なデフォルトメソッドは元のメソッドをオーバーライドし、全く呼び出されないか、再帰的に自分自身を呼び出して無限ループを引き起こす可能性があります。
