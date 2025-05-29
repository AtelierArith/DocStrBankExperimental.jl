```
print_devices()
```

Simple function to print available devices. Calls internal get_backend() function to get the appropriate GPU / CPU backend and prints device information.

# Arguments

  * 'use_gpu':  ('::Bool') If true, check for loaded / functional GPU backends and print appropriate warnings if no GPU backends have been loaded
