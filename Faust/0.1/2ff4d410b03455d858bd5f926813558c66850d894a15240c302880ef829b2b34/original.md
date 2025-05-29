```
init!(d; block_size=256, samplerate=44100)
```

Initializes the DSPBlock `d` for use.

Must be called before `compute!`. The old DSP instance will be deleted, so this can be called repeatedly and will reset internal states, etc.
