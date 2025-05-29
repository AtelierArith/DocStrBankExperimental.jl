This module exports two functions, `adjust_crc` and `adjust_crc!`, which allow you to write 4 bytes to a file or array in order to adjust the 32-bit CRC checksum (either CRC32 or CRC32c) to equal any desired value.

This is useful, for example, to store the checksum of data within the data itself, or simply to set the checksum to be a hard-coded value like `0x01020304` for ease of later checks.
