# Ground Construction

## Introduction

This mod allows you to build any vessel directly on a surface of any planet from a DIY (Do It Yourself) Kit that contains all the high-tech components, needed equipment and blueprints, using only raw materials produced on-site, energy and kerbal workforce.

The major benefit of the Ground Construction is that it allows you to build big, heavy, asymmetrical contraptions that aren't meant to fly at all. Buildings, or even blocks of buildings; heavy rovers; huge rockets held by launch clamps -- all this could be built with Ground Construction anywhere on any planet.

## Features

* **Build anything**: any ship, spaceplane, or really any construction you come up with in Editor. **Even with launch clamps**!
* Build **anywhere on the surface**: the assembled ship will appear right where you've placed the Kit.
* **No complex logistics**, no special production parts required: all you need is a habitable compartment with enough space, raw materials and qualified kerbal personnel.
* **Background operation**: fly other missions while construction takes place on a far-away planet. Days, even weeks may be required to build something complex, but you don't have to babysit your workers.
* **Wireless transfers**: fill the assembled ship with resources and crew before you launch it using dedicated UI.
* **Centralized UI** for progress tracking and fast switching to construction sites.

## Requirements

* [ModuleManager](http://forum.kerbalspaceprogram.com/index.php?/topic/50533-121)
* [CommunityResourcePack](http://forum.kerbalspaceprogram.com/index.php?/topic/83007-12)
* AT_Utils (already included)

## Downloads

* [**Spacedock**](http://spacedock.info/mod/1123/Ground%20Construction) is the main download site for releases
* [GitHub](https://github.com/allista/GroundConstruction) have sources (MIT), assets (CCBY-4.0) and also releases
* CKAN is supported

## How it works

**First**, you need a simple mining operation already running near the spot where you want to build something. So you need: a Drill, an ISRU, some storage tanks for Ore, Metals and any other stuff that you want/need to supply the newly built ship with; some space to work in (hitch-hikers can, science lab or a big passenger compartment will do; we'll call it the *Workshop*) and, last but not least, kerbal engineers that will build things.

**Second**, you need to assemble the DIY Kit with required materials (good luck with finding enough Blutonium for RTG on Minmus), tools and components. This is, fortunately, the simplest thing: in Editor you have a special part, namely the **DIY Kit Container**, which allows you to "load" any previously created and saved ship inside of it. The container is automatically resized to fit its contents, which are much more compact and weight much less than the original ship.

**Third**, you need to attach this container to a carrier or store it in a hold of a cargo ship and fly it across the Void to the construction site.

Then, all that's left is to summon the control UI of the Workshop, deploy the DIY Kit, add it to the construction queue and order the kerbals to work (day and night, no holidays, no weekends!).

## Getting technical

### How a ship is converted into a DIY Kit

In Editor, you add the DIY Kit Container part to the carrier you're building. In its part menu select "Select Vessel" to open the standard vessel selection dialog. Once selected, the ship is loaded into the Kit as follows:

For each part of a ship, its *complexity* is calculated as a function of dry mass, cost and number of modules the part carries. The complexity determines the fraction of part's dry mass that could be manufactured from Metals. Most resources are stripped away. The exceptions are: Solid Fuel, Ablator, all non-tweakable resources (cannot be transfered) and resources with zero density (EC, for one). Everything that's left is packed into the Kit. Thus, a set of Part Kits is produced, which (along with the blueprint of the ship) constitutes the contents of a DIY Kit.

A DIY Kit usually weights much less than a ship that is constructed from it, but, except for the resources, costs almost the same.

### How a DIY Kit is converted back into the (new) ship

First of all, you need to land the kit somewhere on a flat surface, and, preferably, detach it from the carrier. For that DIY Kit Containers are equipped with their own simple decoupling mechanism, which is located on the top side, marked with yellow arrows.

Then you need to *Deploy* the Kit. This could be done by a kerbal in an EVA suit or remotely from a nearby Workshop. A deploying kit **detaches any part** that is still attached to it, then gradually "grows" (imagine that kerbals assemble working scaffolds inside the box) until it have the size of the ship that will be constructed; then it is attached to the surface, so **it cannot be moved any more**.

It doesn't matter how the Kit was oriented. As far as it lies on one of its sides, the deployment dimensions and the orientation of the launched vessel will be automatically chosen to correspond to the surface.

A deployed Kit can be processed by a *nearby* workshop with kerbals, but there are some limitations:

1. The workshop should be **at most** 300m away.
2. The kerbals that will be working on the Kit should be inside the Workshop, not in other parts of the same vessel.
3. These kerbals should be **engineers**. Scientists or pilots don't count.
4. The skill level and number of workers do count: a 5-star engineer works literally as much as five 1-star ones. And five 5-star engineers perform spontaneous miracles.
4. The distance from the Workshop to the Kit affects construction efficiency and, consequently, the time needed. So it's best to make Workshops mobile and get as close to the Kit as possible.
5. The amount of *free space per kerbal* inside the Workshop also affects efficiency: a small compartment with a place for a single kerbal may be **more** efficient than a big one packed with two dozen passenger chairs.
	* **Note 1:** the crewable parts that have Workshop capability have the "Ground Workshop" module (could be seen in part's extended tooltip in Editor), which shows the efficiency of that part.
	* **Note 2:** the efficiency of any generic habitat is capped at 50%. To be more efficient you need to use the provided **Mobile Workshop** part and build a rover with it.
6. If you want to benefit from background construction, you need to make sure you have enough power and Metals to work with, as resources are not generated in the background.

When the Kit is complete, you can "wirelessly" transfer resources and crew to it from the Workshop using dedicated UI. Then you can *Launch* the assembled ship, which will appear at the exact place where the Kit was.