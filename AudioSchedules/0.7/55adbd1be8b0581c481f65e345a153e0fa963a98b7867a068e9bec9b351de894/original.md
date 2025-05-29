```
AudioSchedule(; sample_rate = 44100Hz)
```

Create an empty `AudioSchedule`. You can [`push!`](@ref) new synthesizers to the audio_schedule. Provide 4 arguments to `push!`: the schedule, the synthesizer, the start time, and an envelope that you create with [`@envelope`](@ref).

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

You can iterate over an `AudioSchedule`. Each element will just be a vector of amplitudes.

```jldoctest audio_schedule
julia> length(first(audio_schedule))
44100

julia> length(collect(audio_schedule))
4

julia> collect(AudioSchedule())
Any[]
```

You can use write the audio_schedule directly to a `PortAudio.PortAudioStream`. The `PortAudioStream` must have exactly 1 output channel, and a matching sample rate.

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

You can turn an `AudioSchedule` off in real time by setting `is_on[] = false`, for example,

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

You can save an `AudioSchedule` as a `SampledSignals.SampleBuf`.

```jldoctest audio_schedule
julia> using SampledSignals: SampleBuf


julia> saved = SampleBuf(audio_schedule)
176400-frame, 1-channel SampleBuf{Float64, 1}
4.0s sampled at 44100.0Hz
▃▄▄▄▄▅▅▅▅▅▅▅▅▆▆▆▆▆▆▆▆▆▆▆▆▆▆▅▅▅▅▅▅▅▅▄▄▄▄▃▃▄▄▄▄▅▅▅▅▅▅▅▅▆▆▆▆▆▆▆▆▆▆▆▆▆▆▅▅▅▅▅▅▅▅▄▄▄▄▃
```

You can `empty!` an `AudioSchedule` and reuse it.

```jldoctest audio_schedule
julia> empty!(audio_schedule)

julia> audio_schedule
0.0 s 44100.0 Hz AudioSchedule
```
