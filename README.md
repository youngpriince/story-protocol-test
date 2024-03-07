## Story Protocol
To get started with setting a repository up from scratch, first initialize a project using a package manager. We recommend using yarn. Run the following in a new directory of your choice:
```
yarn init
```

Then, setup foundry using the following command:
```
forge init --force
```

We specify --force since we are initializing within a repository. Once done, do some cleaning up on the dependency management side - we recommend using yarn to manage dependencies directly, so remove those conflicting with forge by running the following:
```
rm -rf lib/ .gitmodules
```

Also, please remove the placeholder test contracts:
```
rm src/Counter.sol test/Counter.t.sol
```

Now, we are ready to start installing our dependencies. To incorporate the Story Protocol core and periphery modules, run the following to have them added to your package.json. We will also install openzeppelin and erc6551 as a dependency for the contract and test.

# note: you can run them one-by-one, or all at once
```
yarn add @story-protocol/protocol-core@beta-rc6
yarn add @story-protocol/protocol-periphery@beta-rc3
yarn add @openzeppelin/contracts
yarn add @openzeppelin/contracts-upgradeable
yarn add erc6551
```

Additionally, for working with Foundry's testkit, we also recommend adding the following as devDependencies:
```
yarn add -D https://github.com/dapphub/ds-test
yarn add -D github:foundry-rs/forge-std#v1.7.6
```

Run yarn. Then, create a file in the root folder named remappings.txt and paste the following:
```
@openzeppelin/=node_modules/@openzeppelin/
@story-protocol/protocol-core=node_modules/@story-protocol/protocol-core/
@story-protocol/protocol-periphery=node_modules/@story-protocol/protocol-periphery/
erc6551/=node_modules/erc6551/
forge-std/=node_modules/forge-std/src/
ds-test/=node_modules/ds-test/src/
```

we are ready to build a simple test registration contract. 
