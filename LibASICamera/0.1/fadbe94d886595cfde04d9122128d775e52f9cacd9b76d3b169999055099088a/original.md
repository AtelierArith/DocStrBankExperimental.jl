```
get_video_data!(id::Integer, buffer, timeout_ms)
```

Writes a video frame to the given buffer. Make sure the buffer is large enough to fit the frame. Call this as fast as possible in a loop and check whether the return value equals ASI_SUCCESS.

# Args:

```
id: Camera id
buffer: A buffer to write the video frame to.
timeout_ms: Time to wait for a frame. Recommendation: 2 * exposure_μs + 500 ms <- inconsistent units?!
```

# Returns:

```
An ASI_ERROR_CODE, which should be ASI_SUCCESS.
```
