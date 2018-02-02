# OSRM
Setting up OSRM server and Using with Leaflet Routing Engine


High performance routing engine written in C++14 designed to run on Open Street Map data.
Documentation Link : https://github.com/Project-OSRM/osrm-backend/wiki
We can setup our own running OSRM server on an Ubuntu machine.
Instructions for Installation : 
Remove everything if you had any previous installation/failed installation.
Go into the build folder of previous install and type
sudo make uninstall
Remove files from previous installation
cd / cd usr cd local cd bin sudo rm osrm-components cd .. cd include rm -R osrm sudo rm -R osrm cd .. cd bin sudo rm osrm-extract sudo rm osrm-parition sudo rm osrm-partition Sudo rm osrm-customize Sudo rm osrm-contract Sudo rm osrm-datastore Sudo rm osrm-routed sudo rm osrm-partition sudo rm osrm-customize sudo rm osrm-contract sudo rm osrm-datastore sudo rm osrm-routed cd .. cd lin sudo rm /usr/local/lib/libosrm.a sudo rm /usr/local/lib/libosrm_extract.a sudo rm /usr/local/lib/libosrm_partition.a sudo rm /usr/local/lib/libosrm_customize.a sudo rm /usr/local/lib/libosrm_update.a sudo rm /usr/local/lib/libosrm_contract.a sudo rm /usr/local/lib/libosrm_store.a sudo rm /usr/local/share/osrm/profiles sudo rm /usr/local/share/osrm/profiles/bicycle.lua sudo rm /usr/local/share/osrm/profiles/debug_example.lua sudo rm /usr/local/share/osrm/profiles/rasterbotinterp.lua sudo rm /usr/local/share/osrm/profiles/examples sudo rm /usr/local/share/osrm/profiles/examples/postgis.lua sudo rm /usr/local/share/osrm/profiles/foot.lua sudo rm /usr/local/share/osrm/profiles/testbot.lua sudo rm /usr/local/share/osrm/profiles/turnbot.lua sudo rm /usr/local/share/osrm/profiles/car.lua sudo rm /usr/local/share/osrm/profiles/lib sudo rm /usr/local/share/osrm/profiles/lib/pprint.lua sudo rm /usr/local/share/osrm/profiles/lib/relations.lua sudo rm /usr/local/share/osrm/profiles/lib/destination.lua sudo rm /usr/local/share/osrm/profiles/lib/utils.lua sudo rm /usr/local/share/osrm/profiles/lib/sequence.lua sudo rm /usr/local/share/osrm/profiles/lib/set.lua sudo rm /usr/local/share/osrm/profiles/lib/access.lua sudo rm /usr/local/share/osrm/profiles/lib/profile_debugger.lua sudo rm /usr/local/share/osrm/profiles/lib/guidance.lua sudo rm /usr/local/share/osrm/profiles/lib/way_handlers.lua sudo rm /usr/local/share/osrm/profiles/lib/maxspeed.lua sudo rm /usr/local/share/osrm/profiles/lib/tags.lua sudo rm /usr/local/share/osrm/profiles/test.lua sudo rm /usr/local/share/osrm/profiles/rasterbot.lua sudo rm /usr/local/lib/pkgconfig/libosrm.pc
Install dependencies
sudo apt-get install git 
sudo apt-get install g++ 
sudo apt-get install cmake 
sudo apt-get install libboost-dev 
sudo apt-get install libboost-filesystem-dev 
sudo apt-get install libboost-thread-dev
sudo apt-get install libboost-system-dev 
sudo apt-get install libboost-regex-dev 
sudo apt-get install libstxxl-dev 
sudo apt-get install libxml2-dev 
sudo apt-get install libsparsehash-dev 
sudo apt-get install libbz2-dev
sudo apt-get install zlib1g-dev 
sudo apt-get install libzip-dev 
sudo apt-get install libgomp1 
sudo apt-get install liblua5.1-0-dev
sudo apt-get install pkg-config 
sudo apt-get install libgdal-dev 
sudo apt-get install libboost-program-options-dev 
sudo apt-get install libboost-iostreams-dev
sudo apt-get install libboost-test-dev 
sudo apt-get install libtbb-dev 
sudo apt-get install libexpat1-dev
sudo apt-get install libluabind-dev
Clone the Project in the home directory of the user.
cd /home/optym/
git clone https://github.com/Project-OSRM/osrm-backend.git
Go to the cloned directory and Build the project
cd osrm-backend
mkdir -p build
cd build
cmake .. -DCMAKE_BUILD_TYPE=Release
cmake --build .
sudo cmake --build . --target install
Download the map needed. Source : http://download.geofabrik.de/
wget http://download.geofabrik.de/europe/germany/berlin-latest.osm.pbf
Extract the routing data. The profile needs to be passed. There can be profiles like car, bike, foot etc.
osrm-extract berlin-latest.osm.pbf -p profiles/car.lua
Contract - Creating the Hierarchy
osrm-contract berlin-latest.osrm
Run the HTTP Server for using APIs
osrm-routed berlin-latest.osrm
Using APIs
The APIs documentation is present here : 
https://github.com/Project-OSRM/osrm-backend/blob/master/docs/http.md
http://project-osrm.org/docs/v5.10.0/api/
We can use tools like POSTMAN or a Web Browser for testing APIs