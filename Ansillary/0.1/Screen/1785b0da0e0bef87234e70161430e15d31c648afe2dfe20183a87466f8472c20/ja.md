このモジュールは、画面に表示される内容を制御することに関するものです。

このモジュールの2つの主要な機能は、代替画面への切り替えと、現在画面に表示されている内容のクリアです。

[代替画面](https://invisible-island.net/xterm/ctlseqs/ctlseqs.html#h2-The-Alternate-Screen-Buffer)は、ほとんどの端末の機能で、アプリケーションがスクロールバックのない画面に切り替えることを可能にし、通常の画面のスクロールバックに干渉することなく端末に描画できるようにします。これは、vimやemacsなどのフルスクリーンアプリケーションに最も便利です。Ansillaryは、[`alternative`](@ref)関数を使用して代替画面に入ることを可能にします：

```julia-repl
julia> Screen.alternative() do
		   println("No scrollback!")
		   read(stdin, UInt8)
	   end
```

Ansillaryは、[`alternative`](@ref)が呼び出されるときに生モード（[非標準モード](https://www.gnu.org/software/libc/manual/html_node/Canonical-or-Not.html)とも呼ばれる）を設定します。これはほとんど常に望ましいものであり、これを避けるには、非公開の[`alternative!`](@ref)および[`standard!`](@ref)関数を使用します。

[`raw`](@ref)関数を使用して生モードのみを設定することも可能です。生モードの主な利点は、入力ストリームが行バッファリングされず、一度に1バイトを読み取ることができる（これによりアプリケーションがキー入力に応答できるようになる）ことと、入力が直接出力に印刷されず、アプリケーションが印刷可能な入力を独自の方法で処理できることです（たとえば、vimスタイルのキー割り当てを実装できるようにするため）。

画面をクリアするために、Ansillaryは[`clear!`](@ref)関数を提供し、どの部分の画面をクリアする必要があるかを指定するための[`Area`](@ref)型も提供します。

この短いスクリプト

```julia
print("Some line...")
move!(Left(3))
clear!(FromCursorForward())
print("!")
```

は、`Some line!`が端末に印刷される結果になります。

このモジュールはまた、`displaysize`の少し良いラッパーとして[`size`](@ref)を提供します。
