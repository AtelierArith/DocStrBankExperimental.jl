```
AudioSchedule(; sample_rate = 44100Hz)
```

空の `AudioSchedule` を作成します。新しいシンセサイザーを audio_schedule に [`push!`](@ref) で追加できます。`push!` に 4 つの引数を提供します：スケジュール、シンセサイザー、開始時間、および [`@envelope`](@ref) で作成したエンベロープです。

```jldoctest audio_schedule
julia> using AudioSchedules

julia> audio_schedule = AudioSchedule()
0.0 s 44100.0 Hz AudioSchedule

julia> push!(audio_schedule, Map(sin, Cycles(440Hz)), 0s, @envelope(
           0,
           Line => 1s,
           0.2,
           Line => 1s,
           0,
       ))

julia> push!(audio_schedule, Map(sin, Cycles(660Hz)), 2s, @envelope(
            0,
            Line => 1s,
            0.2,
            Line => 1s,
            0,
        ))

julia> audio_schedule
4.0 s 44100.0 Hz AudioSchedule
```

`AudioSchedule` を反復処理できます。各要素は振幅のベクトルになります。

```jldoctest audio_schedule
julia> length(first(audio_schedule))
44100

julia> length(collect(audio_schedule))
4

julia> collect(AudioSchedule())
Any[]
```

audio_schedule を `PortAudio.PortAudioStream` に直接書き込むことができます。`PortAudioStream` は正確に 1 つの出力チャネルを持ち、サンプルレートが一致している必要があります。

```jldoctest audio_schedule
julia> using PortAudio: PortAudioStream


julia> PortAudioStream(0, 1, warn_xruns = false) do stream
           write(stream, audio_schedule)
       end

julia> PortAudioStream(0, 2) do stream
            write(stream, audio_schedule)
        end
ERROR: ArgumentError: PortAudioStream does not have 1 output channel
[...]

julia> PortAudioStream(0, 1, samplerate = 48000) do stream
            write(stream, audio_schedule)
        end
ERROR: ArgumentError: Sample rates of PortAudioStream (48000.0) and AudioSchedule (44100.0) do not match
[...]
```

`AudioSchedule` をリアルタイムでオフにするには、`is_on[] = false` を設定します。例えば、

```jldoctest audio_schedule
julia> using Base.Threads: @spawn

julia> using PortAudio: PortAudioStream

julia> @sync begin
            @spawn PortAudioStream(0, 1, warn_xruns = false) do stream
                write(stream, audio_schedule)
            end
            sleep(2)
            audio_schedule.is_on[] = false
        end;
```

`AudioSchedule` を `SampledSignals.SampleBuf` として保存できます。

```jldoctest audio_schedule
julia> using SampledSignals: SampleBuf


julia> saved = SampleBuf(audio_schedule)
176400-frame, 1-channel SampleBuf{Float64, 1}
4.0s sampled at 44100.0Hz
▃▄▄▄▄▅▅▅▅▅▅▅▅▆▆▆▆▆▆▆▆▆▆▆▆▆▆▅▅▅▅▅▅▅▅▄▄▄▄▃▃▄▄▄▄▅▅▅▅▅▅▅▅▆▆▆▆▆▆▆▆▆▆▆▆▆▆▅▅▅▅▅▅▅▅▄▄▄▄▃
```

`AudioSchedule` を `empty!` で空にして再利用できます。

```jldoctest audio_schedule
julia> empty!(audio_schedule)

julia> audio_schedule
0.0 s 44100.0 Hz AudioSchedule
```
