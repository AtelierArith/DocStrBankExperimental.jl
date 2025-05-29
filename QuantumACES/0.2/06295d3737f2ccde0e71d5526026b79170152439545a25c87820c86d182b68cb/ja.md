```
display_circuit(stim_circuit_string::String; without_noise::Bool = true)
display_circuit(qiskit_circuit::Py)
```

提供されたStimまたはQiskit回路`stim_circuit_string`または`qiskit_circuit`を表示し、`without_noise`が`true`の場合は、PauliノイズチャネルなしでStim回路を表示します。注意してください：PythonCallに格納されたPython配列は0からインデックス付けされるため、間違ったQiskit回路にインデックスを付けるのは簡単です。
