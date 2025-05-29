The raw transaction format and several peer-to-peer network messages use a type of variable-length integer to indicate the number of bytes in a following piece of data. Bitcoin Core code refers to these variable length integers as compactSize. Many other documents refer to them as var_int or varInt, but this risks conflation with other variable-length integer encodings—such as the CVarInt class used in Bitcoin Core for serializing data to disk. Because it’s used in the transaction format, the format of compactSize unsigned integers is part of the consensus rules. For numbers from 0 to 252, compactSize unsigned integers look like regular unsigned integers. For other numbers up to 0xffffffffffffffff, a byte is prefixed to the number to indicate its length—but otherwise the numbers look like regular unsigned integers in little-endian order.

|                                   Value | Bytes Used |                                  Format |
| ---------------------------------------:| ----------:| ---------------------------------------:|
|                          >= 0 && <= 252 |          1 |                                 uint8_t |
|                     >= 253 && <= 0xffff |          3 | 0xfd followed by the number as uint16_t |
|             >= 0x10000 && <= 0xffffffff |          5 | 0xfe followed by the number as uint32_t |
| >= 0x100000000 && <= 0xffffffffffffffff |          9 | 0xff followed by the number as uint64_t |

For example, the number 515 is encoded as 0xfd0302.
