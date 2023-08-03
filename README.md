# NSCOM01-RTSP-RTP-Video-Streaming

First, start the server with the command: `python Server.py <server_port>`
where server_port is the port your server listens to for incoming RTSP connections. The standard RTSP port is 554, but you will need to choose a port number greater than 1024.

Then, start the client with the command: `python ClientLauncher.py <server_host> <server_port> <RTP_port> <video_file>`
where server_host is the name of the machine where the server is running, server_port is the port where the server is listening on, RTP_port is the port where the RTP packets are received, and video_file is the name of the video file you want to request (we have provided one example file movie.Mjpeg). The file
format is described in Appendix section.


The client opens a connection to the server and pops up a window like this:
![image](https://github.com/richjpex/NSCOM01-RTSP-RTP/assets/97244148/0167c25c-1963-41ba-9e29-b356e73495a3)

You can send RTSP commands to the server by pressing the buttons. A normal RTSP interaction goes as follows.

1. Client sends SETUP. This command is used to set up the session and transport parameters.
2. Client sends PLAY. This starts the playback.
3. Client may send PAUSE if it wants to pause during playback.
4. Client sends TEARDOWN. This terminates the session and closes the connection.

The server always replies to all the messages the client sends. The reply codes are roughly the same as in HTTP. The code 200 means that the request was successful. In this task, you do not need to implement any other reply codes. For more information about RTSP, please see RFC 2326.

## Appendix
In this task, the server streams a video that has been encoded into a proprietary MJPEG file format. This format stores the video as concatenated JPEG-encoded images, with each image being preceded by a 5-Byte header which indicates the bit size of the image. The server parses the bitstream of the MJPEG file to extract the JPEG images on the fly. The server sends the images to the client at periodic intervals. The client then displays the individual JPEG images as they arrive from the server.
