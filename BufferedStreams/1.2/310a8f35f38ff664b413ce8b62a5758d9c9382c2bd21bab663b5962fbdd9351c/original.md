Fills `buffer` with bytes from `stream`'s buffer without advancing the position.

Unless the buffer is empty, we do not re-fill it. Therefore the number of bytes read is limited to the minimum of `nb` and the remaining bytes in the buffer.
