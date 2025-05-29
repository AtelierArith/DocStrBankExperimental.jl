```
mt_pgram!(output, s::AbstractVector{T}; onesided::Bool=eltype(s)<:Real,
    nfft::Int=nextfastfft(length(s)), fs::Real=1,
    nw::Real=4, ntapers::Int=ceil(Int, 2nw)-1,
    window::Union{AbstractMatrix,Nothing}=nothing) where T<:Number
mt_pgram!(output::AbstractVector, signal::AbstractVector, config::MTConfig) -> Periodogram
```

マルチテーパーのパワースペクトル密度推定を計算し、出力を `output` に格納します。引数:

  * `signal::AbstractVector`: 長さは `config.n_samples` である必要があります
  * `output::AbstractVector`: 長さは `length(config.freq)` である必要があります

オプションで、[`MTConfig`](@ref) オブジェクトを渡して一時変数を事前に割り当て、設定を選択できます。そうでない場合は、キーワード引数を渡して設定を選択できます。

`Periodogram` を返します。

他に [`mt_pgram`](@ref) と [`MTConfig`](@ref) も参照してください。
