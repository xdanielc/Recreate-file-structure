from pathlib import Path

reference = Path(r"D:\Reference") #reference
target = Path(r"D:\Destination") #destination

for folder in reference.glob('**/*'):
    if folder.is_dir():
        referencerel = folder.relative_to(reference) 
        destination = target.joinpath(referencerel) 
        destination.mkdir(mode=0o777, parents=False, exist_ok=True)

stemmap = {}
for file in reference.glob('**/*'):
    if file.is_file():
            # only store the directory the file is in, no need for the filename itself
            # store full stem, we'll decide later what to look at in there
            stemmap[file.stem[:28]] = file.parent.relative_to(reference) #change numb

for file in target.glob('**/*'):
    if file.is_file():
        stem = file.stem[:28] #change numb
        if stem in stemmap:
            rel_path = stemmap[stem]
            # build the new corrected path, inside of
            # target + rel_path of reference + target filename
            corrected_path = target.joinpath(rel_path, file.name)
            # file.rename(corrected_path)
            print(corrected_path)
        else:
            print(file.stem)

print("DONE!")
