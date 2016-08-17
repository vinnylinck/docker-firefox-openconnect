Firefox on a docker container with openconnect installed, nice for who wants to connect on a VPN without messing the local machine netword.

To allow connections on local x11:
```
xhost +local:root # everything is open
xhost -local:root && xhost +local:firefox-vpn # only the firefox container is able to connect
```

To execute the container
```
docker run -d -e DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix --name firefox-vpn --hostname firefox-vpn --privileged tiagodeoliveira/firefox-vpn
```

To setup the VPN:
```
docker exec -it firefox-vpn openconnect --config=/etc/openconnect/openconnect.conf -b myvpn.com
```
===============================================

pode ser para o chrome

[11:10]  
funciona ok

[11:11]  
ele vai pedir uma url do 2nd factor

[11:11]  
`2fv.agcocorp.com`

[11:11]  
e vai logar com o atlanta\something

[11:12]  
`docker exec -it firefox-vpn openconnect --config=/etc/openconnect/openconnect.conf -b myvpn.com`

[11:12]  
este comando ai não vai funcionar

[11:12]  
tem q fazer ele em dois steps

[11:12]  
`docker exec -it firefox-vpn bash` (edited)

[11:12]  
`openconnect --config=/etc/openconnect/openconnect.conf -b navpn.agcocorp.com`
