Start a queue consumer.

queue: queue name consumer*tag: id of the consumer, server generates a unique tag if this is empty no*local: do not deliver own messages no_ack: no acknowledgment needed, server automatically and silently acknowledges delivery (speed at the cost of reliability) exclusive: request exclusive access (only this consumer can access the queue) nowait: do not send a reply method
