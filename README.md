BUILD INSTRUCTIONS
==================



macOS Install 
-------------

With Boost 1.65.0
./bootstrap.sh 
./b2 toolset=darwin install

wget https://sourceforge.net/projects/boost/files/boost/1.65.0/boost_1_65_1.tar.gz/download


??? with Boost 1.66.0


wget https://sourceforge.net/projects/boost/files/boost/1.66.0/boost_1_66_0.tar.gz/download
tar -xzvf download
rm download
cd boost_1_66_0
./bootstrap.sh --with-toolset=clang --with-icu --with-python=python
./b2 toolset=clang install


*nix Install
------------



Windows Install
---------------


 

EXECUTION
=========





CODE LAYOUT
===========
- folders are features (no src/inc)

Minimum Viable Product
======================
* DONE - KEP-??? - executable (Dmitry,Rich) called the_db
* DONE - KEP-99 - parameters etherium address, port, (--addr=<addr> --port=<port>) (Dmitry)
* DONE KEP-100 - ws (Rich) bring in listener, session
* KEP-?? - push model:someone connects to the node, the node pushes messages (Dmitry)
    * services: node info daemon sends this to gui on ws connection

   ```
    {
        "cmd":"updateNodes",
        "seq":123,
        "data":[
        {
            "address":"123.22.22.22",
            "name":"fluffy_kitty",
            "isLeader":true,
            "available":2128,
            "used":228
        }]
    }
    ```

* nodes have ini files: ini file (Mehdi)
    * each instance of daemon should have it's own ini
    * optional command line parameter --ini="name"
    * ~/.bluzelle/.kepler<id>rc
    * id could be port or (port and address) or (name)

ARCHITECHTURE
=============
* node
    * has ini file
    * client connects


LATER
=====

* wss
* https
* nodes can discover friends of nodes and add those addresses to their ini.
* nodes will connect
* nodes will do raft
* update nodes for the nodes the node knows about
* get peers
```
{"cmd":"getPeers", "seq":132}
{"response":"getPeers", "peers": [{"123.22.33.33", "fluffy_bunny"},{"232.22.33.22", "fluffy_puppy"}], "seq":132}
```
* update nodes