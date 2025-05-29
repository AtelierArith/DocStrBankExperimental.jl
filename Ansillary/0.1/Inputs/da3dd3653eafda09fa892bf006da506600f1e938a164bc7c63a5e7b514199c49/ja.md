このモジュールは、ターミナルからイベントを読み取ることに関するものです。

主にこれらのイベントはユーザーからの入力ですが、一部の機能は*ターミナル*がメッセージを送信することにも関係しています。

このモジュールが提供する基本的な機能は、入力ストリームから単一のイベントを読み取ることができることです。

```jldoctest
julia> read(IOBuffer("[7;2~"), Event)
Shift+Home
```

Ansillaryがイベントを認識しない場合、読み取ったバイト*およびストリーム内の残りのバイト*を返します。

```jldoctest
julia> read(IOBuffer("[Q[7;2~"), Event)
Ansillary.Inputs.Unknown(UInt8[0x1b, 0x5b, 0x51, 0x1b, 0x5b, 0x37, 0x3b, 0x32, 0x7e])
```

これは、アプリケーションが実際には未知のイベントの一部であるように見える有効なイベントを受け取るリスクを最小限に抑えるために行われます。**これは完全に確実ではない**ことに注意してください。たとえば、KonsoleはSuper+yが押されたときに`"@sy"`を送信し、Ansillaryはそれを4つの別々のイベントとして喜んで受け入れます。

```jldoctest
julia> let input = IOBuffer("@sy"); [read(input, Event), read(input, Event), read(input, Event), read(input, Event)] end
4-element Array{Ansillary.Inputs.Key,1}:
 Ctrl+x
 @
 s
 y
```

[`Events`](@ref)は`read(::Any, ::Event)`をラップするイテレータであり、これがどのように機能するかはファイル`examples/keylogger.jl`を参照してください。[`EventLoop`](@ref)は、`period`ごとに[`Tick`](@ref)イベントを送信するイテレータでもあり、これがどのように機能するかはファイル`examples/snake.jl`または`tests/interactive.jl`を参照してください（この型のドキュメントの警告にも注意してください）。

このモジュールには、ブラケットペーストモードをオンにする[`paste`](@ref)関数も含まれています。ブラケットペーストモードでは、ユーザーがターミナルに何かをペーストすると、[`PasteStart`](@ref)イベントが送信され、その後にペーストされたテキストが続き、最後に[`PasteEnd`](@ref)イベントが送信されます。

!!! warning
    このモジュールの機能は、ターミナルが生モードである場合にのみ正しく機能します。例えば、

    ```julia
    Screen.raw() do
    	for key in Events(stdin)
    		@show key
    		if key == CTRL_C
    			break
    		end
    	end
    end
    ```

